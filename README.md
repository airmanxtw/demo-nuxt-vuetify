# Nuxt 3 + Vuetify 3

Look at the [nuxt 3 documentation](https://v3.nuxtjs.org) to learn more.

## Setup

1. creating a Nuxt 3 project
```
npx nuxi init nuxt-app
```

2. install Vuetify 3 and sass
```
npm install vuetify@next sass
```
3. install the font
```
npm install @mdi/font
```

4. Create a plugins folder then create a file named vuetify.js
```js
// plugins/vuetify.js
import { createVuetify } from "vuetify";
import { aliases, mdi } from "vuetify/iconsets/mdi";
import * as components from "vuetify/components";
import * as directives from "vuetify/directives";
import "@mdi/font/css/materialdesignicons.css";
import "vuetify/styles";

export default defineNuxtPlugin((nuxtApp) => {
  const vuetify = createVuetify({
    components,
    directives,
    icons: {
      defaultSet: "mdi",
      aliases,
      sets: {
        mdi,
      },
    },
    ssr: true,
  });
  nuxtApp.vueApp.use(vuetify);
});
```

5. tell Nuxt how to properly find and build Vuetify's sass
```js
// nuxt.config.ts
import { defineNuxtConfig } from 'nuxt'
// https://v3.nuxtjs.org/api/configuration/nuxt.config
export default defineNuxtConfig({
  css: ['vuetify/lib/styles/main.sass'],
  build: {
    transpile: ['vuetify'],
  },
})
```

