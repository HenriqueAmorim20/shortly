<template>
  <div>
    <NavDesktop v-if="width > 700" :menu="menu" />
    <NavMobile v-if="width <= 700" :menu="menu" />
  </div>
</template>
<script>
import NavDesktop from "./nav-desktop.vue";
import NavMobile from "./nav-mobile.vue";

export default {
  name: "NavbarLayout",
  components: {
    NavDesktop,
    NavMobile,
  },
  data() {
    return {
      menu: ["features", "pricing", "resources", "login", "sign up",],
      width: null,
    };
  },
  mounted() {
    this.width = window.innerWidth;
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    });
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      this.width = window.innerWidth;
    },
  },
};
</script>
