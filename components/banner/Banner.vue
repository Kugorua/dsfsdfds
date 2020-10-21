<template>
  <div class="banner">
      <div class="banner__container">
           <hooper
            style="height: 100vh; outline: none"
            ref="carousel"
            @slide="updateCarousel"
            :settings="hooperSettings"
           >
                <slide class="slider">
                    <div class="slider__background"><img :src="imgBackground" alt=""></div>
                    <div class="slider__content">
                        <h2>A Perfect Restaurant That Makes Your Dream</h2>
                        <h4>Pickled ethnic farm-to-table distillery ugh chia</h4>
                        <div class="slider__content__btn"><button>Button</button></div>
                    </div>
                </slide>
                <slide class="slider">
                    <div class="slider__background"><img :src="imgBackground" alt=""></div>
                    <div class="slider__content">
                        <h2>A Perfect Restaurant That Makes Your Dream</h2>
                        <h4>Pickled ethnic farm-to-table distillery ugh chia</h4>
                        <div class="slider__content__btn"><button>Button</button></div>
                    </div>
                </slide>
                <slide class="slider">
                    <div class="slider__background"><img :src="imgBackground" alt=""></div>
                    <div class="slider__content">
                        <h2>A Perfect Restaurant That Makes Your Dream</h2>
                        <h4>Pickled ethnic farm-to-table distillery ugh chia</h4>
                        <div class="slider__content__btn"><button>Button</button></div>
                    </div>
                </slide>
                <slide class="slider">
                    <div class="slider__background"><img :src="imgBackground" alt=""></div>
                    <div class="slider__content">
                        <h2>A Perfect Restaurant That Makes Your Dream</h2>
                        <h4>Pickled ethnic farm-to-table distillery ugh chia</h4>
                         <div class="slider__content__btn"><button>Button</button></div>
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
        hooperSettings: {
        infiniteScroll: true,
        itemsToSlide: 1,
        centerMode: true,
        wheelControl: true,
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
console.log( this.carouselData )
    //   this.listSlider = this.listSlider.map((item, index) => {
    //     if (index === this.carouselData) {
    //       return (item = true);
    //     }
    //     return (item = false);
    //   });
    },
  },

}
</script>

<style lang="scss" scoped>
@import "~/assets/scss/components/banner.scss";
</style>