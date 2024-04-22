<template>
  <!-- <el-row :gutter="20">
    <el-col :sm="3" class="hidden-xs-only" style="opacity:0;">左侧占位</el-col>
    <el-col :xs="24" :sm="18">
      <el-container>
        <el-timeline class="animate__animated animate__fadeInLeft">
          <el-timeline-item :color="color" v-for="essay in essayList" :key="essay.id" :timestamp="essay.createTime"
            placement="top">
            <el-card
              style="letter-spacing: 1px;border: 1px solid rgba(255,190,23,0.9); background-color: rgba(255,255,255,0.9);box-shadow: 0 0 30px -10px ">
              <h2 v-if="essay.title" style="color: rgba(255,190,23,0.9);">{{essay.title}}</h2>
              <div v-if="essay.contentType ==='1'" class="typo ql-editor" v-html="essay.content"></div>
              <div v-else v-html="essay.content"></div>
            </el-card>
          </el-timeline-item>
        </el-timeline>
      </el-container>
    </el-col>
    <el-col :sm="3" class="hidden-xs-only" style="opacity:0;">右侧占位</el-col> -->
  <!-- 设置底部距离的 -->
  <!-- <el-backtop :bottom="60">
      <div style="
            height: 50px;
            width: 50px;
            background-color: rgba(240,239,241,1);
            box-shadow: 0 0 6px rgba(0,0,0, .12);
            text-align: center;
            line-height: 40px;
            border-radius:2px;
            color: #1989fa;
          ">
        <svg-icon icon-class="top" />
      </div>
    </el-backtop>
  </el-row> -->

  <el-table :data="tableData" border style="width: 100%;border: 1px solid #ccc;"
    @selection-change="handleSelectionChange">
    <el-table-column prop="id" label="ID" width="80" sortable>
    </el-table-column>
    <el-table-column prop="name" label="内容" sortable>
    </el-table-column>
    <el-table-column prop="date" label="日期" sortable width="180">
    </el-table-column>
  </el-table>

</template>

<script>
  // import 'cherry-markdown/dist/cherry-markdown.min.css'
  //使用prism.js代码高亮
  // import '@/views/cms/plugins/prism.js'
  // import '@/views/cms/plugins/prism.css'
  // import {
  //   cmsEssayList,
  // } from "@/api/cms/blog";
  export default {
    data() {
      return {
        tableData: [
          {
            id: 1,
            date: '2024-04-14',
            name: '随缘更新',
          },
        ],
        multipleSelection: []
      }
    },

    methods: {
      toggleSelection(rows) {
        if (rows) {
          rows.forEach(row => {
            this.$refs.multipleTable.toggleRowSelection(row);
          });
        } else {
          this.$refs.multipleTable.clearSelection();
        }
      },
      handleSelectionChange(val) {
        this.multipleSelection = val;
      }
    }
  }
</script>

<style>

</style>