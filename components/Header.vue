<template>
  <div class="header">
    <div class="header__container">
      <ul class="header__container__select-language" v-if="isShowHideLanguage">
        <li class="header__container__select-language__item" @click="changeLanguage(dataLanguage[1].title)" > <span>{{dataLanguage[1].title}}</span> <img :src="dataLanguage[1].img" alt=""></li>
        <li class="header__container__select-language__item"  @click="changeLanguage(dataLanguage[2].title)"> <span>{{dataLanguage[2].title}}</span> <img :src="dataLanguage[2].img" alt=""></li>
         </ul>
      <div class="header__container__contact">
        <div class="header__container__contact__map">
          <img :src="imgPhoneIcon" alt="">
        </div>
        <div class="header__container__contact__phone">
          <img :src="imgMapIcon" alt="">
        </div>
        <div class="header__container__contact__language">
          <img @click="showHideLanguage" :src="dataLanguage[0].img" alt="">
        </div>
      </div>
      <hr>
      <div class="header__container__body">
        <ul class="header__container__body__list">
          <li class="header__container__body__list__item"> <a href="#" class="active">Home</a> </li>
          <li class="header__container__body__list__item"> <a href="#">About us</a> </li>
          <li class="header__container__body__list__item"><a href="#">menu</a></li>
          <li class="header__container__body__list__item"><a href="#">reservation</a></li>
          <li class="header__container__body__list__item"><a href="#">contact</a></li>
          <li class="header__container__body__list__item"><a href="#">Blog</a></li>
        </ul>
        <div class="header__container__body__search">
          <img :src="imgSearchIcon" alt="">
        </div>
        <div class="header__container__body__card">
          <img :src="imgCartIcon" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import imgPhoneIcon from "../assets/img/phone-icon.png";
import imgCartIcon from "../assets/img/cart-icon.png";
import imgMapIcon from "../assets/img/map-icon.png";
import imgLanguageIcon from "../assets/img/language-icon.png";
import imgSearchIcon from "../assets/img/search-icon.png";
import imgKorea from "../assets/img/korea.png";
import imgVietnam from "../assets/img/vietnam.png";
let dataLanguage=[{
  img:imgLanguageIcon,
  title:"English"
},
{
  img:imgKorea,
  title:"Korea"
},
{
  img:imgVietnam,
  title:"Vietnammes"
},
]
export default {
data:()=>{
  return{
    imgPhoneIcon,imgCartIcon,imgMapIcon,imgLanguageIcon,imgSearchIcon,imgKorea,imgVietnam,
    isShowHideLanguage:false,
    dataLanguage
  }
},
methods:{
  showHideLanguage(){
    this.isShowHideLanguage=!this.isShowHideLanguage
  },
  changeLanguage(value){
    let i=0;
    let dataLanguageChange=[...this.dataLanguage];
    this.isShowHideLanguage=!this.isShowHideLanguage
    for(let item of this.dataLanguage){
      if(value===item.title){
        dataLanguageChange[0]=item
        dataLanguageChange[i]=this.dataLanguage[0]
      } i+=1
    }
    this.dataLanguage=[...dataLanguageChange]
  }
}
}
</script>
<style lang="scss" scoped>
@import "~/assets/scss/layout/header.scss";
</style>