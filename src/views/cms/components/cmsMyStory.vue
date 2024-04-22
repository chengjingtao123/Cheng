<template>
  <el-container>
    <div class="background">
      <video autoplay muted loop controlsList="nodownload noremoteplayback" :src="videoSource" class="video-background"
        style="width: 100%;
              object-fit:fill;"></video>
    </div>
    <el-table :data="tableData" border style="width: 100%;border: 1px solid #ccc;"
      @selection-change="handleSelectionChange">
      <el-table-column prop="id" label="ID" width="80" sortable>
      </el-table-column>
      <el-table-column prop="name" label="内容" sortable>
      </el-table-column>
      <el-table-column prop="date" label="日期" sortable width="180">
      </el-table-column>
    </el-table>
  </el-container>
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
        videoSources: [
          require('@/assets/images/bg1.mp4'), // 例如，这里使用require导入视频路径
          require('@/assets/images/bg2.mp4'),
        ],
        videoSource: '', // Initially empty
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
    created() {
      // Choose a random video source
      const randomIndex = Math.floor(Math.random() * this.videoSources.length)
      this.videoSource = this.videoSources[randomIndex]
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
  .el-footer {
    background-color: rgba(84, 92, 100, 0.5);
  }

  .background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    z-index: -1;
  }

  .video-background::-webkit-media-controls {
    display: none !important;
  }

  .video-background {
    min-width: 100%;
    min-height: 100%;
    width: auto;
    height: auto;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: -1;
  }

  /* Media queries for responsiveness */
  @media only screen and (max-width: 768px) {
    .video-background {
      width: 100%;
      height: auto;
    }
  }

  @media only screen and (max-width: 576px) {
    .video-background {
      height: 100%;
      width: auto;
    }
  }
</style>