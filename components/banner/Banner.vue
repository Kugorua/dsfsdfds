<template>
  <div class="banner">
      <div class="banner__container">
        <ul class="banner__container__dots">
          <li
            v-for="(item, index) in listSlider"
            :key="index"
            class="banner__container__dots__item"
            
            @click.prevent="slideTo(index)"
          >
           <div class="banner__container__dots__item__line" 
           :class="{'banner__container__dots__item__active': item }"></div>
           <span> {{index + 1}} </span>
         </li>
    </ul>

           <hooper
            style="height: 100vh; outline: none"
            ref="carousel"
            @slide="updateCarousel"
            :settings="hooperSettings"
           >
                <slide class="slider" v-for="(item, index) in listSlider"
            :key="index">
                    <div class="slider__background"><img :src="imgBackground" alt=""></div>
                    <div class="slider__content">
                        <h2 :class="{'slider__content__title-1':item}">A Perfect Restaurant That Makes Your Dream</h2>
                        <h4 :class="{'slider__content__title-2':item}">Pickled ethnic farm-to-table distillery ugh chia</h4>
                        <div class="slider__content__btn" :class="{'slider__content__btn-anm':item}" ><button>Button</button></div>
                    </div>
                </slide>
               
                
           </hooper>
         
      </div>
  </div>
</template>

<script>
import imgBackground from "../../assets/img/Bitmap.png";
export default {
data:()=>{
    return{
        imgBackground,
         listSlider: [true, false, false, false],
        hooperSettings: {
        infiniteScroll: true,
        itemsToSlide: 1,
        centerMode: true,
        wheelControl: false,
        // autoPlay: true,
        // hoverPause: false,
        // playSpeed: 10000,
        // transition: 400,
      },
    }
},
methods: {
    slideTo(item) {
      this.$refs.carousel.slideTo(item);
    },
    updateCarousel(payload) {
      this.carouselData = payload.currentSlide;
      if (payload.currentSlide === 4) {
        this.carouselData = 0;
      } else if (this.carouselData === -1) {
        this.carouselData = 3;
      }
      this.listSlider = this.listSlider.map((item, index) => {
        if (index === this.carouselData) {
          return (item = true);
        }
        return (item = false);
      });
    },
  },
}
</script>

<style lang="scss" scoped>
@import "~/assets/scss/components/banner.scss";
</style>  