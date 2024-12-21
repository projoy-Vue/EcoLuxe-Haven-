<template>
  <div class="home">
    <HeroSection />
    <ProductComponent/>
    <CategoryComponent/>
    <TestimonialsComponent/>
    <NewsletterSignup/>
    <SustainabilitySection/>
  </div>
</template>

<script>
import ProductComponent from "@/components/ProductComponent.vue";
import HeroSection from "../components/HeroSection.vue";
import CategoryComponent from "@/components/CategoryComponent.vue";
import TestimonialsComponent from "@/components/TestimonialsComponent.vue";
import NewsletterSignup from "@/components/NewsletterSignup.vue";
import SustainabilitySection from "@/components/SustainabilitySection.vue";

export default {
  name: "Home",

  components: {
    HeroSection,
    ProductComponent,
    CategoryComponent,
    TestimonialsComponent,
    NewsletterSignup,
    SustainabilitySection
  },

};
</script>

<style scoped>

</style>
