<template>
  <div id="app">
    <VueCookieConsent></VueCookieConsent>
  </div>
</template>

<script>
import VueCookieConsent from "./Banner.vue";
// import VueCookieConsent from "../dist/vue-cookie-consent.common";

export default {
  components: {
    VueCookieConsent
  }
};
</script>
<style>
body {
  font-family: "Roboto", sans-serif;
}
</style>
