<template>
  <div>
    <transition name="loading">
      <div class="page-container" v-if="loadingShow">
        <div id="loading-panel">
          {{percent}}
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
  export default {
    name: "loading",
    data() {
      return {
        count: 0,
        percent: '',
        loadingShow: true,
        imgs: [
          "static/img/achievement-btn.png",
          "static/img/apple.png",
          "static/img/close-btn.png",
          "static/img/getseed-btn.png",
          "static/img/index-bg1.jpg",
          "static/img/index-bg2.png",
          "static/img/index-tree-bg.jpg",
          "static/img/index-tree-bg1.jpg",
          "static/img/olduser.png",
          "static/img/pay-btn.png",
          "static/img/pick.png",
          "static/img/pop-apple.png",
          "static/img/pop-close-btn.png",
          "static/img/pop-tree.png",
          "static/img/realname-err.png",
          "static/img/realname-success.png",
          "static/img/rules-btn.png",
          "static/img/seed.png",
          "static/img/tree.png",
          "static/img/tree-light.png",
          "static/img/tree-mature-bg.jpg",
          "static/img/tree-over-bg.jpg",
          "static/img/unselect-img.png",
          "static/img/watering.png",
          "static/img/watering-btn.png",
          "static/img/num-0.png",
          "static/img/num-1.png",
          "static/img/num-2.png",
          "static/img/num-3.png",
          "static/img/num-4.png",
          "static/img/num-5.png",
          "static/img/num-6.png",
          "static/img/num-7.png",
          "static/img/num-8.png",
          "static/img/num-9.png"
        ]
      }
    },
    mounted: function () {
      this.preload()
    },
    methods: {
      preload: function () {
        for (let img of this.imgs) {
          let image = new Image()
          image.src = img;
          image.onload = () => {
            this.count++;
            // 计算图片加载的百分数，绑定到percent变量
            let percentNum = Math.floor(this.count / (this.imgs.length - 1) * 100)
            this.percent = `${percentNum}%`
          }
        }
      },

    },

    watch: {
      count: function (val) {
        if (val === this.imgs.length - 1) {
          // 图片加载完成后隐藏
          this.loadingShow = false;

        }
      }
    }
  }
</script>
<style scoped>
  .page-container {
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    font-size: 14px;
    z-index: 99999;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #2F9B30;
  }

  #loading-panel {
    width: 170px;
    height: 170px;
    line-height: 170px;
    background: url("../../static/img/loading.gif") center center no-repeat;
    background-size: 100% 100%;
    text-align: center;
    color: #fff;
  }

  .loading-enter, .loading-leave-to {
    opacity: 0;
  }

  .loading-enter-to, .loading-leave {
    opacity: 1;
  }

  .loading-enter-active, .loading-leave-active {
    transition: all 0.5s;
  }

</style>
