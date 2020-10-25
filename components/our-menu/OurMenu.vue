<template>
  <div class="our-menu">
      <div class="our-menu__container">
          <div class="our-menu__container__description">
              <div class="our-menu__container__description__img-1" >
                  <img :src="imgView1" alt="">
              </div>
              <div class="our-menu__container__description__img-2" >
                  <img :src="imgView2" alt="">
              </div>
          </div>
          <div class="our-menu__container__introduce">
                <h3 class="our-menu__container__introduce__name">
                  Awesome Menu
                </h3>
                <h2 class="our-menu__container__introduce__title">Our Food Menus</h2>
                <div class="line" ></div>
                <p class="our-menu__container__introduce__content">Queequeg's broad canvas belt, and fast to my narrow leather one. So that for better or for worse, we two, for the time, were wedded; and should poor Queequeg sink to rise no more.</p>
                
                <div class="our-menu__container__introduce__btn" >
                    <button><span>see all menu</span>  </button>
                </div>
          </div>
          
      </div>
  </div>
</template>

<script>
import imgArowRigth from "../../assets/img/Arrow-right.png";
import imgView1 from "../../assets/img/food-1.png";
import imgView2 from "../../assets/img/food-2.png";
export default {
data:()=>{
    return{
        imgArowRigth,
        imgView1,
        imgView2
    }
}
}
</script>

<style lang="scss" scoped>
@import "~/assets/scss/components/our-menu.scss";
</style>  