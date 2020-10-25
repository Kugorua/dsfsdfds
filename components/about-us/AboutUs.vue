<template>
  <div class="about-us">
      <div class="about-us__container">
          <div class="about-us__container__introduce">
                <h3 class="about-us__container__introduce__name">
                    About Us
                </h3>
                <h2 class="about-us__container__introduce__title">Our Story</h2>
                <div class="line" ></div>
                <p class="about-us__container__introduce__content">It was a humorously perilous business for both of us. For, before we proceed further, it must be said that the monkey-rope was fast at both ends.</p>
                <p class="about-us__container__introduce__content">Queequeg's broad canvas belt, and fast to my narrow leather one. So that for better or for worse, we two, for the time, were wedded; and should poor Queequeg sink to rise no more, then both usage and honour demanded.</p>
                <div class="about-us__container__introduce__btn" >
                    <button><span>Discover More</span> <img :src="imgArowRigth" alt=""> </button>
                </div>
          </div>
          <div class="about-us__container__description">
              <div class="about-us__container__description__img-1" >
                  <img :src="imgView1" alt="">
              </div>
              <div class="about-us__container__description__img-2" >
                  <img :src="imgView2" alt="">
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import imgArowRigth from "../../assets/img/Arrow-right.png";
import imgView1 from "../../assets/img/view-1.png";
import imgView2 from "../../assets/img/view-2.png";
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
@import "~/assets/scss/components/about-us.scss";
</style>  