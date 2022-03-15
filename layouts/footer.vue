<template>
  <div>
    <footer class="footer">
      <section class="logo">
        <v-img class="logo-img" :src="require('@/static/logo.svg')"></v-img>
      </section>
      <section class="menu">
        <ul v-for="(column, index) in menu" :key="index" class="menu-list">
          <li class="menu-list-title">{{ column.title }}</li>
          <li
            v-for="(row, index) in column.items"
            :key="index"
            class="menu-list-item"
          >
            {{ row }}
          </li>
        </ul>
      </section>
      <section class="media">
        <v-img
          v-for="(src, index) in media"
          :key="index"
          class="media-img"
          :src="require(`@/static/icon-${src}.svg`)"
        ></v-img>
      </section>
    </footer>
  </div>
</template>
<script>
export default {
  name: "FooterLayout",
  data() {
    return {
      menu: [
        {
          title: "features",
          items: ["link shortening", "branded links", "analytics"],
        },
        {
          title: "resources",
          items: ["blog", "developers", "support"],
        },
        {
          title: "company",
          items: ["about", "our team", "careers", "contact"],
        },
      ],
      media: ["facebook", "twitter", "pinterest", "instagram"],
    };
  },
};
</script>
<style scoped>
.footer {
  background-color: var(--VeryDarkViolet);
  display: grid;
  grid-template-columns: 0.65fr 1fr 0.5fr;
  gap: 1.5rem;
  padding: 5% 10%;
}

.menu {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}

.logo-img {
  max-width: 100px !important;
}

.menu-list {
  list-style: none;
  font-size: 0.9rem;
}

.menu-list-title {
  color: var(--White);
  font-weight: 700;
  text-transform: capitalize;
  margin-bottom: 1rem;
}

.menu-list-item {
  font-size: 0.8rem;
  color: var(--GrayishViolet);
  text-transform: capitalize;
  margin-bottom: 0.5rem;
}

.media {
  display: flex;
  justify-content: space-evenly;
}

.media-img {
  max-width: 20px !important;
  max-height: 20px !important;
}

@media (max-width: 800px) {
  .footer {
    grid-template-columns: 1fr;
    gap: 2.5rem;
  }
}

@media (max-width: 500px) {
  .menu {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .menu-list {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 0;
  }

  .logo {
    display: flex;
    justify-content: center;
  }

}
</style>
