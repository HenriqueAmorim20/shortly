<template>
  <v-app-bar class="navbar" flat color="#fff" height="60">
    <v-img class="logo-img" :src="require('@/static/logo-dark.svg')"></v-img>
    <v-spacer></v-spacer>
    <v-menu bottom left offset-y :close-on-content-click="drawer">
      <template v-slot:activator="{ on, attrs }">
        <v-icon
          class="navbar-icon"
          color="hsl(257, 27%, 26%)"
          v-bind="attrs"
          v-on="on"
          >mdi-menu
        </v-icon>
      </template>
      <v-list class="menu-items">
        <v-list-item v-for="index in 3" :key="index">
          <v-list-item-title class="menu-item">{{ menu[index - 1] }}</v-list-item-title>
        </v-list-item>
        <span class="divider"></span>
        <v-list-item>
          <v-list-item-title class="menu-item">{{ menu[3] }}</v-list-item-title>
        </v-list-item>
        <v-list-item>
          <v-list-item-title class="menu-item-auth">{{ menu[4] }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
  </v-app-bar>
</template>
<script>
export default {
  name: "NavMobileLayout",
  props: {
    menu: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      drawer: true,
    };
  },
};
</script>
<style scoped>
.navbar {
  padding: 0.5rem 5%;
  color: var(--DarkViolet) !important;
}
.logo-img {
  max-width: 100px !important;
}

.navbar-icon {
  font-size: 2rem;
}

.menu-items {
  background: var(--DarkViolet) !important;
  color: var(--White) !important;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem 0;
  border-radius: 0.5rem;
}

.menu-item {
  font-size: 0.9rem;
  color: var(--White);
  font-weight: 700;
  text-transform: capitalize;
}

.menu-item-auth {
  font-size: 0.9rem;
  font-weight: 700;
  color: var(--White);
  background-color: var(--Cyan);
  padding: 0.5rem 6rem;
  width: 100%;
  border-radius: 1rem;
  text-transform: capitalize;
}

.divider {
  width: 90%;
  border-bottom: 1px solid rgba(255, 255, 255, 0.267);
}
</style>
