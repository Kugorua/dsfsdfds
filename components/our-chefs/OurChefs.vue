<template>
  <div class="chefs">
    <div class="chefs__container">
      <div class="chefs__container__title">
        
        <p>Our Team</p>
        
        <h2>Meet our talent Chefs</h2>
        <div class="chefs__container__title__line"></div>
      </div>
      <div class="chefs__container__slider">
        <button class="chefs__container__slider__btn-prev" @click.prevent="slidePrev">
            <svg width="25" height="55" viewBox="0 0 43 77" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M43 71.4641L38.2972 77L0 38.5L38.2972 0L43 5.03268L9.5 38.2484L43 71.4641Z" fill="#8E959B"/>
            </svg>
        </button>
        <button class="chefs__container__slider__btn-next" @click.prevent="slideNext">
            <svg width="25" height="55" viewBox="0 0 43 77" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M0 71.4641L4.70283 77L43 38.5L4.70283 0L0 5.03268L33.5 38.2484L0 71.4641Z" fill="#8E959B"/>
            </svg>
        </button>
        <hooper
          ref="carousel"
          :settings="hooperSettings"
          style="height: auto; outline: none"
          @slide="updateCarousel"
        >
          <slide
            class="slider"
            v-for="(item, index) in dataSlideItem"
            :key="index"
          >
            <div class="slider__items">
              <div
                class="slider__container"
                :class="{ 'active-chefs': item.state }"
              >
                <img
                  class="slider__container__img"
                  :class="{ slider__container__act: item.state }"
                  :src="item.img"
                  alt=""
                />
                <div class="slider__container__item">
                  <p class="slider__container__item__price">{{ item.price }}</p>
                  <!-- 1 -->
                  <p class="slider__container__item__name">{{ item.name }}</p>
                </div>
              </div>
            </div>
          </slide>
        </hooper>
      </div>
    </div>
  </div>
</template>

<script>

import imgchefs1 from "../../assets/img/Chef1.jpg";
import imgchefs2 from "../../assets/img/Chef2.png";
import imgchefs3 from "../../assets/img/Chef3.png";
import imgchefs4 from "../../assets/img/Chef4.png";
let dataSlideItem = [
  { img: imgchefs1, price: "Mark Tucker", name: "Demi chef", state: false },
  { img: imgchefs2, price: "Charles Banks", name: "Sous Chef", state: true },
  { img: imgchefs3, price: "Denise Montgomery", name: "CDP Chef", state: false },
  { img: imgchefs4, price: "Denise Montgomery", name: "CDP Chef", state: false },
];
export default {
  data() {
    return {
      imgchefs1,
      imgchefs2,
      imgchefs3,
      imgchefs4,
      countSlider: 0,
      carouselData: 0,
      dataSlideItem,
      hooperSettings: {
        infiniteScroll: true,
        itemsToSlide: 1,
        wheelControl: false,
        breakpoints: {
          1024: {
            itemsToShow: 3,
          },
          768: {
            itemsToShow: 3,
          },
          414: {
            itemsToShow: 1,
          },
        },
      },
    };
  },
  watch: {
    carouselData() {
      this.$refs.carousel.slideTo(this.carouselData);
    },
  },
  methods: {
    slideTo(item) {
      this.$refs.carousel.slideTo(item);
    },
    slidePrev() {
      this.$refs.carousel.slidePrev();
    },
    slideNext() {
      this.$refs.carousel.slideNext();
    },
    updateCarousel(payload) {
      this.carouselData = payload.currentSlide;
      if (payload.currentSlide === 4) {
        this.carouselData = 0;
      } else if (this.carouselData === -1) {
        this.carouselData = 3;
      }
      console.log(this.carouselData);
      this.dataSlideItem = this.dataSlideItem.map((item, index) => {
        this.carouselDatas = this.carouselData + 1;
        if (this.carouselDatas === 4) {
          this.carouselDatas = 0;
        }
        if (index === this.carouselDatas) {
          return { ...item, state: true };
        }
        return { ...item, state: false };
      });
    },
  },
};
</script>
<style lang="scss" scoped>
@import "~/assets/scss/components/chefs.scss";

@keyframes boxShaddow {
  from {
    box-shadow: 0px 0px 0px rgba(0, 0, 0, 0);
  }
  to {
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.4);
  }
}
</style>
