<template>
  <div class="testimonials">
    <div class="testimonials__container">
      <div class="testimonials__container__introduce">
        <h3>Testimonials</h3>
        <h2>People Say About Us</h2>
        <div class="line-white"></div>
        <ul class="testimonials__container__introduce__star">
          <li><img :src="imgStar" alt="" /></li>
          <li><img :src="imgStar" alt="" /></li>
          <li><img :src="imgStar" alt="" /></li>
          <li><img :src="imgStar" alt="" /></li>
          <li><img :src="imgStar" alt="" /></li>
        </ul>
      </div>
      <div
        class="testimonials__container__content"
        v-for="(item, index) in dataInforChefs"
        :key="index"
        v-if="index === indexChef"
      >
        <div
          class="testimonials__container__content__list"
          :class="{ testimonials__container__content__show: item.state }"
        >
          <p
            class="testimonials__container__content__list__text"
            :class="{
              testimonials__container__content__list__salce: item.state,
            }"
          >
            {{ dataInforChefs[indexChef].content }}
          </p>
          <p
            class="testimonials__container__content__list__name"
            :class="{
              testimonials__container__content__list__salce: item.state,
            }"
          >
            {{ dataInforChefs[indexChef].name }}
          </p>
        </div>
      </div>
      <ul class="testimonials__container__avatar">
        <li
          class="testimonials__container__avatar__item-1"
          :class="
            isSet === 0
              ? 'testimonials__container__avatar__item-1'
              : isSet === 1
              ? dataImg[0]
              : dataImg1[0]
          "
        >
          <img :src="imgAvt1" alt="" />
        </li>

        <li
          class="testimonials__container__avatar__item-2"
          :class="
            isSet === 0
              ? 'testimonials__container__avatar__item-2'
              : isSet === 1
              ? dataImg[1]
              : dataImg1[1]
          "
        >
          <img :src="imgAvt2" alt="" />
        </li>
        <li
          class="testimonials__container__avatar__item-3"
          :class="
            isSet === 0
              ? 'testimonials__container__avatar__item-3'
              : isSet === 1
              ? dataImg[2]
              : dataImg1[2]
          "
        >
          <img :src="imgAvt3" alt="" />
        </li>
        <li
          class="testimonials__container__avatar__left"
          @click="changeLeft(1)"
        ></li>
        <li
          class="testimonials__container__avatar__rigth"
          @click="changeLeft(2)"
        ></li>
      </ul>
    </div>
  </div>
</template>

<script>
import imgAvt1 from "../../assets/img/av1.png";
import imgAvt2 from "../../assets/img/av2.png";
import imgAvt3 from "../../assets/img/av3.png";
import imgStar from "../../assets/img/star.png";

let dataImg = [
  "testimonials__container__avatar__move-31",
  "testimonials__container__avatar__move-12",
  "testimonials__container__avatar__move-23",
];
//[31,12,23] ,
let dataImg1 = [
  "testimonials__container__avatar__move-21",
  "testimonials__container__avatar__move-32",
  "testimonials__container__avatar__move-13",
];
let dataInforChefs = [
  {
    name: "anthony nguyen",
    content:
      "“ So that for better or for worse, we two, for the time, were wedded; and should poor Queequeg sink to rise no more, then both usage and honour demanded was my own. “",
    state: false,
  },
  {
    name: "anthony Pham",
    content:
      "“ So that for better or for worse, we two, for the time, were wedded; and should poor Queequeg sink to rise no more, then both usage and honour demanded was my own. “",
    state: true,
  },
  {
    name: "anthony Ho",
    content:
      "“ So that for better or for worse, we two, for the time, were wedded; and should poor Queequeg sink to rise no more, then both usage and honour demanded was my own. “",
    state: false,
  },
];
export default {
  data: () => {
    return {
      imgAvt1,
      imgAvt2,
      imgAvt3,
      imgStar,
      dataImg,
      dataImg1,
      isSet: 1,
      dataInforChefs,
      indexChef: 1,
    };
  },
  methods: {
    changeLeft(index) {
      let dataImgSub = [...this.dataImg];
      let dataImgSub1 = [...this.dataImg1];
      this.isSet = index;

      if (index === 1) {
        dataImgSub = dataImgSub.map((item, index) => {
          if (index === 2) {
            return this.dataImg[0];
          }
          return this.dataImg[index + 1];
        });
        dataImgSub1 = dataImgSub1.map((item, index) => {
          if (index === 2) {
            return this.dataImg1[0];
          }
          return this.dataImg1[index + 1];
        });

        this.indexChef = dataImgSub.indexOf(
          "testimonials__container__avatar__move-12"
        );
      } else {
        dataImgSub1 = dataImgSub1.map((item, index) => {
          if (index === 0) {
            return this.dataImg1[2];
          }
          return this.dataImg1[index - 1];
        });
        dataImgSub = dataImgSub.map((item, index) => {
          if (index === 0) {
            return this.dataImg[2];
          }
          return this.dataImg[index - 1];
        });
        this.indexChef = dataImgSub1.indexOf(
          "testimonials__container__avatar__move-32"
        );
      }
      this.dataInforChefs = this.dataInforChefs.map((item, index) => {
        if (index === this.indexChef) {
          return { ...item, state: true };
        }
        return { ...item, state: false };
      });

      this.dataImg = [...dataImgSub];
      this.dataImg1 = [...dataImgSub1];
    },
  },
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/components/testimonials.scss";
.testimonials {
  background-image: url("../../assets/img/bg-testimation.png");
  background-size: cover;
  background-repeat: no-repeat;
}
</style>
