<template>
  <v-app-bar class="navbar" height="80" flat color="#fff">
    <v-img class="logo-img" :src="require('@/static/logo-dark.svg')"></v-img>
    <span v-for="index in 3" :key="index" class="menu-item">
      {{ menu[index - 1] }}
    </span>
    <v-spacer></v-spacer>
    <span class="menu-item">{{ menu[3] }}</span>
    <span class="menu-item-auth">{{ menu[4] }}</span>
  </v-app-bar>
</template>
<script>
export default {
  name: "NavDesktopLayout",
  props: {
    menu: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
.navbar {
  max-width: 80%;
  margin: 0 auto;
  padding-top: 1rem;
  color: var(--DarkViolet) !important;
}
.logo-img {
  max-width: 100px !important;
  margin-right: 2rem;
}

.menu-item {
  font-size: 0.9rem;
  color: var(--GrayishViolet);
  font-weight: 700;
  text-transform: capitalize;
  margin: 0 1rem;
  cursor: pointer;
}

.menu-item:hover {
  color: var(--DarkViolet);
}

.menu-item-auth {
  font-size: 0.9rem;
  color: var(--White);
  background-color: var(--Cyan);
  padding: 0.4rem 1.5rem;
  border-radius: 1rem;
  text-transform: capitalize;
  margin-left: 1rem;
  cursor: pointer;
}

.menu-item-auth:hover {
  opacity: 0.7;
}

@media (max-width: 850px) {
  .navbar {
    max-width: 90%;
  }
}
@media (max-width: 750px) {
  .navbar {
    max-width: 95%;
  }
}
</style>
