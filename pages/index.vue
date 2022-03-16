<template>
  <div class="main">
    <FirstSection />
    <!-- <SecondSection /> -->
  </div>
</template>

<script>
import FirstSection from "@/sections/first.vue";
// import SecondSection from "@/sections/second.vue";

export default {
  name: "IndexPage",
  components: {
    FirstSection,
    // SecondSection,
  },
};
</script>

<style>
.main {
  padding: 0 10%;
  overflow: hidden;
  background-color: #eff1f7;
  /* background: linear-gradient(#ffffff 50%, #eff1f7 50%); */
  color: var(--GrayishViolet);
}

@media (max-width: 700px) {
  .main {
    padding: 0 5%;
  }
}
</style>
