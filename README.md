# vue-cookie-consent

![](https://i.imgur.com/0A3O6s1.png)

## Install

`npm install vue-cookies-consent`

```
// yourVueFile.vue

import VueCookieConsent from "vue-cookies-consent";

export default {
  components: {
    VueCookieConsent
  }
}
```

## Base usage

```
// any .vue file
// For this example the component is imported in App.vue

<template>
  <div id="app">
    <VueCookieConsent></VueCookieConsent>
  </div>
</template>
```

The component will check for a existing cookie consent in the browsers localStorage on
`mounted()`.
If no consent was found, the banner will show.

# Slots

### Default slot

```
<VueCookieConsent>
 <div>
   This will replace the main text and all stylings relevant to the text
 </div>
</VueCookieConsent>
```

### Link slot

```
<VueCookieConsent>
  <template v-slot:link>
    <div>
      This will replace the "Learn more" link and all stylings relevant to the link
    </div>
  </template>
</VueCookieConsent>
```

### Button slot

```
<VueCookieConsent>
  <template v-slot:button>
    <button>
      This will replace the consent-button and all stylings relevant to the button
    </button>
  </template>
</VueCookieConsent>
```

# Properties

| Property name  | Type    | Default                                                                           |
| -------------- | ------- | --------------------------------------------------------------------------------- |
| text           | String  | "This website uses cookies to ensure you get the best experience on our website." |
| linkText       | String  | "Learn more"                                                                      |
| buttonText     | String  | "Got it"                                                                          |
| storageName    | String  | "cookieConsent"                                                                   |
| preventConsent | Boolean | false                                                                             |

# Examples

## Overwriting text but keeping default styling

```
<VueCookieConsent text="This is my new main text" link-text="Click here for more info" button-text="Okay">
</VueCookieConsent>
```

This result in the following banner:<br />
![Banner with custom text](https://i.imgur.com/CNUgAax.png)

## Changing the localStorage value

```
<VueCookieConsent storage-name="myCustomNameInLocalStorage">
</VueCookieConsent>
```

## Prevent consent and emit event instead

```
<VueCookieConsent prevent-consent @consented="yourHandler">
</VueCookieConsent>
```

Note: The emit does not pass any data.

## Changing the containers styling

No `!important` is being used. You can simply add your own classes to overwrite any existing CSS.

```
<template>
  <VueCookieConsent class="bg-salmon"></VueCookieConsent>
</template>

<style>
.bg-salmon {
  background-color: salmon;
}
</style>
```

Result: <br />
![Banner with custom background color](https://i.imgur.com/TykenXn.png)
