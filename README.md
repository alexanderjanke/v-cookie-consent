# v-cookie-consent

![](https://i.imgur.com/0A3O6s1.png)

## Install

`npm install v-cookie-consent`

```
// yourVueFile.vue

import CookieConsent from "v-cookie-consent";

export default {
  components: {
    CookieConsent
  }
}
```

## Base usage

```
// any .vue file
// For this example the component is imported in App.vue

<template>
  <div id="app">
    <CookieConsent></CookieConsent>
  </div>
</template>
```

The component will check for a existing cookie consent in the browsers localStorage on
`mounted()`.
If no consent was found, the banner will show.

# Slots

### Default slot

```
<CookieConsent>
 <div>
   This will replace the main text and all stylings relevant to the text
 </div>
</CookieConsent>
```

### Link slot

```
<CookieConsent>
  <template v-slot:link>
    <div>
      This will replace the "Learn more" link and all stylings relevant to the link
    </div>
  </template>
</CookieConsent>
```

### Button slot

```
<CookieConsent>
  <template v-slot:button>
    <button>
      This will replace the consent-button and all stylings relevant to the button
    </button>
  </template>
</CookieConsent>
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
<CookieConsent text="This is my new main text" link-text="Click here for more info" button-text="Okay">
</CookieConsent>
```

This result in the following banner:<br />
![Banner with custom text](https://i.imgur.com/CNUgAax.png)

## Changing the localStorage value

```
<CookieConsent storage-name="myCustomNameInLocalStorage">
</CookieConsent>
```

## Prevent consent and emit event instead

```
<CookieConsent prevent-consent @consented="yourHandler">
</CookieConsent>
```

Note: The emit does not pass any data.

## Changing the containers styling

No `!important` is being used. You can simply add your own classes to overwrite any existing CSS.

```
<template>
  <CookieConsent class="bg-salmon"></CookieConsent>
</template>

<style>
.bg-salmon {
  background-color: salmon;
}
</style>
```

Result: <br />
![Banner with custom background color](https://i.imgur.com/TykenXn.png)
