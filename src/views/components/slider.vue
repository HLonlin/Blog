<template>
  <div class="slider-wrapper">
    <div class="slider__slides">
      <div v-for="(item,i) in adlist" class="slide" :class="{'s--active':i==0}" :key="i" :data-slide="i+1">
        <div class="slide__inner" :style="{backgroundImage: 'url(' + item.imgUrl + ')' }">
          <div class="slide__content__box">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "slider",
    data() {
      return {
        slidingBlocked: false,
        numOfSlides: 0,
      };
    },
    beforeCreate() {},
    created() {},
    beforeMount() {},
    props: {
      adlist: {
        type: Array,
        default: [{
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
        ]
      },
      autoPlayTime: {
        type: Number,
        default: 2000
      },
    },
    mounted() {
      this.slider()
    },
    beforeUpdate() {},
    updated() {},
    beforeDestroy() {},
    destroyed() {},
    methods: {
      slider() {
        let that = this;
        let slides = document.getElementsByClassName('slide');
        let controls = document.getElementsByClassName('slider__control');
        let inner = document.getElementsByClassName('slide__inner');
        that.numOfSlides = slides.length;
        for (let i = 0, imax = slides.length; i < imax; i++) {
          let index = i + 1;
          slides[i].classList.add('slide-' + index);
        }
        that.autoPlaySilder();
      },
      autoPlaySilder() { //自动轮播
        let that = this;
        if (that.slidingBlocked || that.adlist.length <= 0) return;
        that.slidingBlocked = true;
        let $curActive = document.querySelector('.slide.s--active');
        let index = $curActive.dataset.slide;
        let timer_out = setTimeout(function() {
          index++;
          if (index > that.numOfSlides) index = 1;
          let $newActive = document.querySelector('.slide-' + index);
          $curActive.classList.remove('s--active');
          $newActive.classList.add('s--active');
          that.slidingBlocked = false;
          clearTimeout(timer_out);
          that.autoPlaySilder();
        }, that.autoPlayTime);
      }
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .slider-wrapper {
    width: 100%;
    height: 100%;
    overflow: hidden;
  }

  .slider__slides {
    position: relative;
    width: 100%;
    height: 100%;
  }

  .slide {
    position: absolute;
    width: 100%;
    height: 100%;
    transition: clip-path 0s ease 0.8s;
    clip-path: circle(0% at 50% 50%);
  }

  .slide.s--active {
    z-index: 1;
    transition: clip-path 0.8s ease;
    clip-path: circle(100% at 50% 50%);
  }

  .slide__inner {
    position: absolute;
    width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center center;
    background-repeat: no-repeat;
  }

  .slide__inner:before {
    content: "";
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.3);
  }

  .slide__content__box {
    position: relative;
    width: 100%;
    height: 100%;
  }

  @media (max-width: 1024px) and (min-width: 641px) {
    .slider-wrapper {
      height: 50%;
    }
  }

  @media (max-width: 640px) {
    .slider-wrapper {
      height: 50%;
    }
  }
</style>
