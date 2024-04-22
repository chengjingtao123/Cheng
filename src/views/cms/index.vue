<!-- <template>
  <el-container>
    <div class="background" :style="backgroundImage"></div>
    <cmsNavBar></cmsNavBar>
    <keep-alive>
      <cmsMain></cmsMain>
    </keep-alive>
    <el-footer height="40px">
      <cmsFooter></cmsFooter>
    </el-footer>
  </el-container>
</template>
<script>
  import cmsMain from './main.vue'
  import cmsNavBar from './NavBar.vue'
  import cmsFooter from './Footer.vue'
  // 引入背景图
  import backgroundImages from './backgroundImages.js'

  export default {
    data() {
      return {
        backgroundImages,
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }
    },
    components: {
      cmsMain,
      cmsNavBar,
      cmsFooter
    },
    computed: {
      backgroundImage() {
        // 根据背景图数组的长度随机选择索引
        const randIndex = Math.floor(Math.random() * this.backgroundImages.length)
        return {
          // 获取对应的图片资源并将其设置到`background-image`属性上
          backgroundImage: `url(${this.backgroundImages[randIndex]})`
        }
      }
    },
  }
</script>

<style scoped>
  .el-footer {
    background-color: rgba(84, 92, 100, 0.5);
  }

  .background {
    background-repeat: no-repeat;
    background-size: cover;
    margin: 0px;
    padding: 0px;
    top: 0;
    width: 100%;
    height: 120vh;
    position: fixed;
    z-index: -1;
  }

  @media screen and (max-width: 768px) {
    .title {
      width: 100%;
      background-position-x: center;
      background-position-y: 0;
    }
  }
</style> -->

<template>
  <el-container>
    <div class="background">
      <video autoplay muted loop controlsList="nodownload noremoteplayback" :src="videoSource" class="video-background"
        style="width: 100%;
            object-fit:fill;"></video>
    </div>
    <cmsNavBar></cmsNavBar>
    <keep-alive>
      <cmsMain></cmsMain>
    </keep-alive>
    <el-footer height="40px">
      <cmsFooter></cmsFooter>
    </el-footer>
  </el-container>
</template>

<script>
  import cmsMain from './main.vue'
  import cmsNavBar from './NavBar.vue'
  import cmsFooter from './Footer.vue'
  // Import video source
  import videoSource1 from '../../assets/images/bg1.mp4'
  import videoSource2 from '../../assets/images/bg2.mp4'
  export default {
    components: {
      cmsMain,
      cmsNavBar,
      cmsFooter
    },
    data() {
      return {
        videoSources: [videoSource1, videoSource2],
        videoSource: '' // Initially empty
      }
    },
    created() {
      // Choose a random video source
      const randomIndex = Math.floor(Math.random() * this.videoSources.length)
      this.videoSource = this.videoSources[randomIndex]
    }
  }
</script>

<style scoped>
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