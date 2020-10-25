<template>
  <div class="home">
    <Banner />
    <AboutUs />
    <Gallery />
    <OurMenu />
    <Testimonials />
    <OurChefs />
  </div>
</template>

<script>
import Banner from "../components/banner/Banner";
import AboutUs from "../components/about-us/AboutUs";
import Gallery from "../components/gallery/Gallery";
import OurMenu from "../components/our-menu/OurMenu";
import Testimonials from "../components/testimonials/Testimonials";
import OurChefs from "../components/our-chefs/OurChefs";
export default {
  head: {
    title: "Home Page",
  },
};
</script>

<style lang="scss" scoped></style>
