<template>
  <MyHeader></MyHeader>
  <MyBanner></MyBanner>
  <HowItWorks></HowItWorks>
  <ThirdBlock></ThirdBlock>
  <MyReviews></MyReviews>
</template>

<script>
import MyHeader from "./components/Header.vue";
import MyBanner from "./components/Banner.vue";
import HowItWorks from "./components/HowItWorks.vue";
import ThirdBlock from "./components/ThirdBlock.vue";
import MyReviews from "./components/Reviews.vue";

export default {
  name: 'App',
  components: {
    MyHeader,
    MyBanner,
    HowItWorks,
    ThirdBlock,
    MyReviews,
  }
}
</script>