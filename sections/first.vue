<template>
  <section class="first-section">
    <div class="content">
      <h1 class="content-title">more than just shorter links</h1>
      <p class="content-info">
        Build your brand's recognition and get detailed insights on how your
        links are performing.
      </p>
      <span class="content-btn" @click="goTo()">get started</span>
    </div>
    <div class="side-img">
      <v-img
        class="img"
        :src="require('@/static/illustration-working.svg')"
      ></v-img>
    </div>
  </section>
</template>
<script>
export default {
  name: "FirstSection",
  methods: {
    goTo() {
      const element = document.getElementById("second-section");
      const y = element?.getBoundingClientRect().top + window.pageYOffset - 60;
      window.scrollTo({ top: y, behavior: "smooth" });
    },
  },
};
</script>
<style scoped>
.first-section {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 8vw;
  padding: 0 10% 2rem;
}

@media (max-width: 700px) {
  .first-section {
    padding: 0 5%;
  }
}

.content,
.side-img {
  width: 45%;
  max-width: 770px;
}

.side-img .img {
  transform: scale(1.4) translate(5rem, -1rem);
}

.content-title {
  color: var(--VeryDarkViolet);
  font-size: clamp(2rem, 4.5vw, 4rem);
  line-height: 110%;
}

.content-title::first-letter {
  text-transform: uppercase;
}

.content-info {
  font-size: clamp(0.9rem, 1.4vw, 1.6rem);
  margin: 0.5rem 0 2.5rem !important;
}

.content-btn {
  font-size: clamp(0.9rem, 1.4vw, 1.6rem);
  color: var(--White);
  background-color: var(--Cyan);
  padding: 0.7rem 2rem;
  border-radius: 1.5rem;
  font-weight: 700;
  text-transform: capitalize;
  cursor: pointer;
}

.content-btn:hover {
  opacity: 0.7;
}

@media (max-width: 700px) {
  .first-section {
    flex-direction: column-reverse;
  }
  .content,
  .side-img {
    width: 100%;
    margin: 2rem 0;
  }

  .content {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .content-title,
  .content-info {
    text-align: center;
  }

  .side-img .img {
    transform: scale(1.2) translate(3rem, 0) !important;
  }
}
</style>
