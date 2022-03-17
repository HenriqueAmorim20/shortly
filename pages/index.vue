<template>
  <div class="main">
    <FirstSection />
    <SecondSection />
    <ThirdSection />
  </div>
</template>

<script>
import FirstSection from "@/sections/first.vue";
import SecondSection from "@/sections/second.vue";
import ThirdSection from "@/sections/third.vue";

export default {
  name: "IndexPage",
  components: {
    FirstSection,
    SecondSection,
    ThirdSection,
  },
};
</script>

<style>
.main {
  overflow: hidden;
  background-color: #fff;
  color: var(--GrayishViolet);
}
</style>
