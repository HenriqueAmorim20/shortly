<template>
  <v-app class="app">
    <v-main>
      <Nuxt />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@500;700&display=swap');

:root {
  /* ### Primary */

  --Cyan: hsl(180, 66%, 49%);
  --DarkViolet: hsl(257, 27%, 26%);

  /* ### Secondary */

  --Red: hsl(0, 87%, 67%);

  /* ### Neutral */

  --Gray: hsl(0, 0%, 75%);
  --GrayishViolet: hsl(257, 7%, 63%);
  --VeryDarkBlue: hsl(255, 11%, 22%);
  --VeryDarkViolet: hsl(260, 8%, 14%);
}

.app {
  background-color: #fff !important;
  color: var(--DarkViolet) !important;
}
</style>
