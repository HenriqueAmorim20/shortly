<template>
  <section class="third-section">
    <div class="header">
      <h1>Advanced Statistics</h1>
      <p>
        Track how your links are performing across the web with our advanced
        statistics dashboard.
      </p>
    </div>
    <div class="statistics">
      <div class="card-wrapper">
        <v-card light class="card" flat>
          <div class="card-img">
            <v-img
              :src="require('@/static/icon-brand-recognition.svg')"
              width="50"
            ></v-img>
          </div>
          <h3>Brand Recognition</h3>
          <p>
            Boost your brand recognition with each click. Generic links don't
            mean a thing. Branded links help instil confidence in content.
          </p>
        </v-card>
      </div>
      <div class="card-wrapper">
        <v-card light class="card" flat>
          <div class="card-img">
            <v-img
              :src="require('@/static/icon-detailed-records.svg')"
              width="50"
            ></v-img>
          </div>
          <h3>Detailed Records</h3>
          <p>
            Gain insights into who is clicking your links. Knowing when and
            where people engage with your content helps inform better decisions.
          </p>
        </v-card>
      </div>
      <div class="card-wrapper">
        <v-card light class="card" flat>
          <div class="card-img">
            <v-img
              :src="require('@/static/icon-fully-customizable.svg')"
              width="50"
            ></v-img>
          </div>
          <h3>Fully Customizable</h3>
          <p>
            Improve brand awareness content discoverability through customizable
            links, supercharging audience engagement
          </p>
        </v-card>
      </div>
    </div>
    <div class="bottom">
      <h1>Boost your links today</h1>
      <span class="bottom-btn" @click="goTo()">get started</span>
    </div>
  </section>
</template>
<script>
export default {
  name: "ThirdSection",
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
.third-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #eff1f7;
  padding: 4rem 10% 0;
}

@media (max-width: 700px) {
  .third-section {
    padding: 4rem 5% 0;
  }
}

.header {
  text-align: center;
  max-width: 500px;
}

.header h1 {
  font-size: clamp(1.6rem, 5vw, 2rem);
  color: var(--VeryDarkViolet);
  margin-bottom: 1rem;
}

.header p {
  font-size: clamp(0.8rem, 2vw, 1rem);
}

.statistics {
  display: flex;
  padding: 4rem 0;
}

.card-wrapper {
  display: flex;
  margin: 0 1.3rem;
  position: relative;
}

.card-wrapper:nth-child(2n) {
  margin-top: 2rem;
}

.card-wrapper:nth-child(2n)::before {
  position: absolute;
  top: 40%;
  left: -2.6rem;
  z-index: 999;
  display: block;
  content: "";
  border-bottom: 5px solid var(--Cyan);
  width: 2.6rem;
}

.card-wrapper:nth-child(2n)::after {
  position: absolute;
  top: 60%;
  right: -2.6rem;
  z-index: 999;
  display: block;
  content: "";
  border-bottom: 5px solid var(--Cyan);
  width: 2.6rem;
}

.card-wrapper:nth-child(3n) {
  margin-top: 4rem;
}

.card {
  display: flex;
  flex-direction: column;
  padding: 2rem;
  max-width: 350px;
  height: max-content;
}

.card-img {
  width: fit-content;
  background-color: var(--DarkViolet);
  border-radius: 50% !important;
  padding: 1rem;
  margin-top: calc(-4.5rem);
  margin-bottom: 2rem;
}

.card p {
  color: var(--GrayishViolet);
  margin-top: 1rem;
  font-size: 0.9rem;
}

.bottom {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 125%;
  padding: max(3vw, 1.5rem) 0;
  background-color: var(--DarkViolet);
  background-image: url("@/static/bg-boost-desktop.svg");
  background-size: cover;
}

.bottom h1 {
  font-size: clamp(1.5rem, 2.5vw, 2rem);
  color: white;
}

.bottom-btn {
  font-size: clamp(0.9rem, 1.4vw, 1.6rem);
  color: var(--White);
  background-color: var(--Cyan);
  padding: 0.5rem 1.5rem;
  border-radius: 1.5rem;
  margin-top: 1.5rem;
  font-weight: 700;
  text-transform: capitalize;
  cursor: pointer;
}

.bottom-btn:hover {
  background-color: hsl(180, 56%, 62%);
}

@media (max-width: 1100px) {
  .statistics {
    flex-direction: column;
    padding: 0;
  }

  .card-wrapper {
    margin: 5rem 0;
  }

  .card {
    align-items: center;
    text-align: center;
  }

  .card-wrapper:nth-child(2n) {
    margin-top: 0rem;
  }

  .card-wrapper:nth-child(2n)::before {
    position: absolute;
    top: -5rem;
    left: calc(50% - 3px);
    z-index: 999;
    display: block;
    content: "";
    border-right: 6px solid var(--Cyan);
    height: 2.5rem;
    width: 0;
  }

  .card-wrapper:nth-child(3n)::before {
    position: absolute;
    top: -5rem;
    left: calc(50% - 3px);
    z-index: 999;
    display: block;
    content: "";
    border-right: 6px solid var(--Cyan);
    height: 2.5rem;
    width: 0;
  }

  .card-wrapper:nth-child(2n)::after {
    display: none;
  }

  .card-wrapper:nth-child(3n) {
    margin-top: 0rem;
  }
}
</style>
