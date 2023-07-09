# vite-bootstrap-vue

- [Starting with Bootstrap-Vue step by step](https://www.ma-no.org/en/programming/javascript/starting-with-bootstrap-vue-step-by-step)
- [Compatibildad Vue 3 - Vite con Bootstrap-Vue, Font-Awesome, etc](https://platzi.com/tutoriales/1856-avanzado-vue/23120-compatibildad-vue-3-vite-con-bootstrap-vue-font-awesome-etc/)
- [BootstrapVue with @vue/compat - StackBlitz](https://stackblitz.com/edit/bootstrap-vue-with-compat?file=vite.config.js)

- `npm create vite@latest vite-vue3-bootstrap-vue`
- `cd vite-vue3-bootstrap-vue`
- `npm install`
- `npm run dev`
- http://localhost:5173/
- `npm install bootstrap-vue bootstrap@4.3.1`

```js
// vite.config.js

import { fileURLToPath, URL } from 'node:url'

import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    vue({
      template: {
        compilerOptions: {
          compatConfig: {
            MODE: 2
          }
        }
      }
    }),
  ],
  resolve: {
    alias: {
      vue: '@vue/compat',
      '@': fileURLToPath(new URL('./src', import.meta.url))
    }
  }
})

```

```js
// src\main.js

import './assets/main.css'

// import { createApp } from 'vue'
import Vue, { createApp } from "@vue/compat";
import App from './App.vue'
import router from './router'

/*--------------------REGISTER BOOTSTRAP---------------------------------*/
import { BootstrapVue, IconsPlugin } from "bootstrap-vue";
// Import Bootstrap an BootstrapVue CSS files (order is important)
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
// Make BootstrapVue available throughout your project
Vue.use(BootstrapVue);
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin);
/*-----------------------------------------------------------------------*/

const app = createApp(App)

app.use(router)

app.mount('#app')

```

