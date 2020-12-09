<template>
  <div class="app-wrapper">
    <div class="app-sidebar">
      <div class="shade"></div>
    </div>
    <div class="content-wrapper">
      <!-- slides -->
      <slider :adlist="adlist" :autoPlayTime="autoPlayTime"></slider>
      <!-- slides end -->
    </div>
  </div>
</template>

<script>
  import slider from "../components/slider.vue"
  export default {
    name: "layout",
    components: {
      slider,
    },
    data() {
      return {
        adlist: [{
            imgUrl: 'https://img.zcool.cn/community/01468e5fa0ba4b11013fdcc729b7d6.jpg@1280w_1l_2o_100sh.jpg'
          },
          {
            imgUrl: 'https://img.zcool.cn/community/01ecca5fa0a36e11013ee04d092fad.jpg@1280w_1l_2o_100sh.jpg'
          },
          {
            imgUrl: 'https://img.zcool.cn/community/01d1a65f11b470a8012066214f45ee.jpg@1280w_1l_2o_100sh.jpg'
          },
          {
            imgUrl: 'https://img.zcool.cn/community/01d6e05f11b472a801215aa0f7469e.jpg@1280w_1l_2o_100sh.jpg'
          },
          {
            imgUrl: 'https://img.zcool.cn/community/01eabf5ee77633a801215aa0eff8fd.jpg@1280w_1l_2o_100sh.jpg'
          },
          {
            imgUrl: 'https://img.zcool.cn/community/016e305ec2af00a801207200cf2ee8.jpg@1280w_1l_2o_100sh.jpg'
          }
        ],
        autoPlayTime: 2000,
      };
    },
    beforeCreate() {},
    created() {},
    beforeMount() {},
    mounted() {},
    beforeUpdate() {},
    updated() {},
    beforeDestroy() {},
    destroyed() {},
    methods: {},
    computed: {}
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .app-wrapper {
    width: 100%;
    height: 100vh;
    overflow: hidden;
    background-color: #FFFFFF;
  }

  .app-sidebar {
    position: absolute;
    left: 0rem;
    width: 18.75rem;
    height: 100%;
    background-color: #FFFFFF;
    box-shadow: 0px 0px 5px 0px #cccccc;
    background-image: url(../../assets/images/catbg.jpg);
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  .shade{
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(51,51,51,0.7);
  }

  .content-wrapper {
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    padding-left: 18.75rem;
  }



  @media (max-width: 1024px) and (min-width: 641px) {
    .app-sidebar {
      top: 0rem;
      width: 100%;
      height: 5rem;
    }

    .content-wrapper {
      padding-top: 5rem;
      padding-left: 0rem;
    }


  }

  @media (max-width: 640px) {
    .app-sidebar {
      bottom: 0rem;
      width: 100%;
      height: 3.4375rem;
      box-shadow: 0px 0px 2px 0px #cccccc;
    }

    .content-wrapper {
      padding-left: 0rem;
    }

  }
</style>
