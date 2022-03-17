<template>
  <section
    class="second-section"
    id="second-section"
    :class="resultLink ? 'background-linear' : ''"
  >
    <div class="shortener">
      <v-text-field
        light
        placeholder="Shorten a link here..."
        solo
        hide-details=""
        v-model="input"
        flat
        class="input"
        :class="error ? 'error' : ''"
        @keyup="error = !input && input.length < 0"
      ></v-text-field>
      <v-btn :loading="loading" class="section-btn" @click="shortenIt()"
        >shorten it!</v-btn
      >
    </div>
    <div v-if="showResult" class="result">
      <span class="initial-link">{{ initialLink }}</span>
      <v-spacer></v-spacer>
      <a target="_blank" :href="resultLink" class="result-link">{{
        resultLink
      }}</a>
      <span
        class="result-btn"
        :class="copied ? 'copied' : ''"
        @click="copy()"
        >{{ copied ? "copied!" : "copy" }}</span
      >
    </div>
  </section>
</template>
<script>
export default {
  name: "SecondSection",
  data() {
    return {
      input: null,
      error: false,
      showResult: false,
      initialLink: null,
      resultLink: null,
      copied: false,
      loading: false,
    };
  },
  methods: {
    async shortenIt() {
      if (!this.input) return (this.error = true);
      this.loading = true;
      try {
        const response = await this.$axios.$get("/shorten?url=" + this.input);
        this.initialLink = this.input;
        this.error = false;
        this.showResult = true;
        this.resultLink = response.result.full_short_link;
      } catch (error) {
        this.error = true;
      }
      this.loading = false;
    },

    copy() {
      const el = document.createElement("textarea");
      el.value = this.resultLink;
      el.setAttribute("readonly", "");
      el.style.position = "absolute";
      el.style.left = "-9999px";
      document.body.appendChild(el);
      el.select();
      document.execCommand("copy");
      document.body.removeChild(el);
      this.copied = true;
      setTimeout(() => {
        this.copied = false;
      }, 3000);
    },
  },
};
</script>
<style scoped>
.second-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 6rem 10% 0;
  background: linear-gradient(#ffffff 70%, #eff1f7 70%);
}

.background-linear {
  background: linear-gradient(#ffffff 50%, #eff1f7 50%);
}

@media (max-width: 700px) {
  .second-section {
    padding: 1rem 5% 0;
    background: linear-gradient(#ffffff 50%, #eff1f7 50%);
  }

  .background-linear {
    background: linear-gradient(#ffffff 30%, #eff1f7 30%);
  }
}

.shortener {
  max-width: 1440px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--DarkViolet);
  background-image: url("@/static/bg-shorten-desktop.svg");
  background-size: cover;
  background-position: center;
  border-radius: 0.7rem;
  padding: clamp(1.5rem, 3vw, 3rem) clamp(1.5rem, 3.5vw, 3.5rem);
}

.input {
  width: 100% !important;
}

.error {
  border: 2px solid hsla(0, 100%, 72%, 0.52) !important;
  position: relative;
  animation: horizontal-shaking 0.2s;
}

@keyframes horizontal-shaking {
  0% {
    transform: translateX(0);
  }
  25% {
    transform: translateX(5px);
  }
  50% {
    transform: translateX(-5px);
  }
  75% {
    transform: translateX(5px);
  }
  100% {
    transform: translateX(0);
  }
}

.error::before {
  position: absolute;
  bottom: -1.6rem;
  left: 0;
  display: block;
  content: "Please add a link";
  color: hsla(0, 100%, 72%, 0.719);
  font-style: italic;
  font-size: 0.9rem;
}

.section-btn {
  font-size: clamp(0.9rem, 1.2vw, 1rem);
  color: var(--White);
  background-color: var(--Cyan) !important;
  padding: 1.5rem 1.8rem !important;
  border-radius: 0.3rem !important;
  font-weight: 700;
  text-transform: capitalize;
  cursor: pointer;
  margin-left: 1.5rem;
}

.section-btn:hover {
  background-color: hsl(180, 56%, 62%) !important;
}

.result {
  display: flex;
  align-items: center;
  background-color: #fff;
  border-radius: 0.25rem;
  padding: clamp(0.8rem, 2vw, 1.6rem) clamp(1.6rem, 3vw, 3.2rem);
  margin: 1rem 0 0;
}

.initial-link {
  overflow: scroll;
  white-space: nowrap;
  font-size: clamp(0.7rem, 1.2vw, 1rem);
  color: var(--VeryDarkViolet);
}

.result-link {
  font-size: clamp(0.7rem, 1.2vw, 1rem);
  color: var(--Cyan);
  text-decoration: none;
  margin-left: 1.5rem;
}

.result-btn {
  font-size: clamp(0.7rem, 1.2vw, 1rem);
  color: var(--White);
  background-color: var(--Cyan);
  padding: clamp(0.5rem, 0.5vw, 1.6rem) clamp(1rem, 2.5vw, 3.2rem);
  border-radius: max(0.35vw, 0.3rem);
  font-weight: 700;
  text-transform: capitalize;
  cursor: pointer;
  margin-left: 1.5rem;
}

.result-btn:hover {
  background-color: hsl(180, 56%, 62%);
}

.copied {
  color: white;
  background-color: var(--DarkViolet);
}

.copied:hover {
  background-color: var(--DarkViolet) !important;
}

@media (max-width: 700px) {
  .shortener {
    flex-direction: column;
  }

  .section-btn {
    width: 100% !important;
    margin: 2rem 0 0;
  }

  .error::before {
    bottom: -1.6rem;
  }

  .result {
    flex-direction: column;
    align-items: flex-start;
  }

  .initial-link {
    width: 100%;
  }

  .result-btn {
    width: 100%;
    margin: 0;
    text-align: center;
  }

  .result-link {
    margin: 0.5rem 0;
    width: 100%;
  }

  .result-link::before {
    display: block;
    content: "";
    border-top: 1px solid rgba(128, 128, 128, 0.137);
    padding-bottom: 0.5rem;
  }
}
</style>
