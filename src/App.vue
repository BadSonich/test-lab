<template>
  <SiteHeader></SiteHeader>
  <SiteBanner></SiteBanner>
  <HowItWorks></HowItWorks>
  <ThirdBlock></ThirdBlock>
  <SiteReviews></SiteReviews>
  <SiteFaq></SiteFaq>
  <BlockSix></BlockSix>
  <SiteForm></SiteForm>
  <SiteFooter></SiteFooter>
</template>

<script>
import SiteHeader from "@/components/Header.vue";
import SiteBanner from "@/components/Banner.vue";
import HowItWorks from "@/components/HowItWorks.vue";
import ThirdBlock from "@/components/ThirdBlock.vue";
import SiteReviews from "@/components/Reviews.vue";
import SiteFaq from "@/components/Faq.vue";
import BlockSix from "@/components/BLockSIx.vue";
import SiteForm from "@/components/Form.vue";
import SiteFooter from "@/components/Footer.vue";

export default {
  name: 'App',
  components: {
    SiteHeader,
    SiteBanner,
    HowItWorks,
    ThirdBlock,
    SiteReviews,
    SiteFaq,
    BlockSix,
    SiteForm,
    SiteFooter,
  }
}
</script>