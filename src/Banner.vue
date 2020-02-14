<template>
  <div v-if="show" class="consent-wrapper p-4 fixed shadow-md">
    <slot>
      <div class="pb-1">
        {{ text }}
      </div>
    </slot>
    <slot name="link">
      <div class="pb-3">
        <a
          class="consent-link"
          :href="link ? link : `https://www.cookiesandyou.com/`"
          target="_blank"
        >
          {{ linkText }}
        </a>
      </div>
    </slot>
    <slot name="button">
      <div
        class="consent-button p-2 bg-blue-700  
        text-white text-center rounded cursor-pointer"
        @click="consent"
      >
        {{ buttonText }}
      </div>
    </slot>
  </div>
</template>
<script>
export default {
  props: {
    text: {
      type: String,
      default:
        "This website uses cookies to ensure you get the best experience on our website."
    },
    linkText: {
      type: String,
      default: "Learn more"
    },
    link: String,
    buttonText: {
      type: String,
      default: "Got it"
    },
    storageName: {
      type: String,
      default: "cookieConsent"
    },
    preventConsent: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      show: false
    };
  },
  mounted() {
    this.checkConsent();
  },
  methods: {
    checkConsent() {
      const consent = localStorage.getItem(this.storageName);
      if (consent == "true") this.show = false;
      else this.show = true;
    },
    consent() {
      if (this.preventConsent) this.$emit("consented");
      else {
        localStorage.setItem(this.storageName, "true");
        this.checkConsent();
      }
    }
  }
};
</script>
<style>
.shadow-md {
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.06);
}
.fixed {
  position: fixed;
}
.p-2 {
  padding: 0.5rem;
}
.p-4 {
  padding: 1rem;
}
.pb-1 {
  padding-bottom: 0.25rem;
}
.pb-3 {
  padding-bottom: 0.75rem;
}
.rounded {
  border-radius: 0.25rem;
}
.text-white {
  color: #fff;
}
.text-center {
  text-align: center;
}

.bg-blue-700 {
  background-color: #2b6cb0;
}
.cursor-pointer {
  cursor: pointer;
}
.consent-wrapper {
  right: 10px;
  bottom: 10px;
}

.consent-button:hover {
  background-color: #3182ce;
}

@media (min-width: 640px) {
  .consent-wrapper {
    width: 24rem;
  }
}
@media only screen and (max-width: 639px) {
  .consent-wrapper {
    right: 0;
    bottom: 0;
  }
}
.consent-link {
  color: #000;
  opacity: 0.6;
  text-decoration: none;
  transition: filter 0.1s ease-in-out;
}
.consent-link:hover {
  filter: invert(0.15);
}
</style>
