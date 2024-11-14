<div align="center">
  <a href="https://khulnasoft.com">
    <img
      src="https://avatars.githubusercontent.com/u/56705483"
      alt="ReadyAPI Logo"
      height="64"
    />
  </a>
</div>
<div align="center">

# ReadyAPI UI <font size=2><sup>ALPHA</sup></font>

</div>

Welcome to readyapi-ui, a collection of presentational components for our web applications. This library is built using [Vue 3](https://v3.vuejs.org/) and [Tailwind CSS](https://tailwindcss.com/). Preview the components in [Histoire](https://ui.khulnasoft.com/).

## Installation

To install the library in your project, run the following command:

```bash
pnpm add @readyapi/ui
```

## Setup

In your `main.ts` file, import the library and register it as a plugin:

```ts
import { createApp } from "vue"
import App from "./App.vue"
// Import the library
import { plugin as HoppUI } from "@readyapi/ui"

// Import theme styles for default styling (optional)
import "@readyapi/ui/themes.css"

// Import the styles
import "@readyapi/ui/style.css"

const app = createApp(App)

// Register the library as a plugin
app.use(HoppUI)

app.mount("#app")
```

The Library uses Tailwind CSS under the hood, so you have to import the preset in your `tailwind.config.ts` file:

```ts
import preset from "@readyapi/ui/ui-preset"

export default {
  content: ["src/**/*.{vue,html}"],
  presets: [preset],
}
```

## Usage

You can use the components in your Vue templates like this:

```ts
<template>
  <HoppButtonPrimary label="Click me" />
</template>

<script lang="ts" setup>
import { HoppButtonPrimary } from "@readyapi/ui"
</script>
```

If you're using `unplugin-vue-components` in your project, you can import the components like this without having to import them in the script section:

```ts
<template>
  <HoppButtonPrimary label="Click me" />
</template>

<script lang="ts" setup>
</script>
```

To configure resolve options for `unplugin-vue-components`, add the following to your `vite.config.ts` file:

```ts
import { defineConfig } from "vite"
import vue from "@vitejs/plugin-vue"
import Components from "unplugin-vue-components/vite"

export default defineConfig({
  plugins: [
    vue(),
    Components({
      resolvers: [
        // auto import components
        (name) => {
          if (name.startsWith("Hopp")) {
            return {
              importName: name,
              path: "@readyapi/ui",
            }
          }
        },
      ],
    }),
  ],
})
```

## Histoire

We've included Histoire in this library which is similar to Storybook, to make it easy to play with the components in the browser. You can run Histoire in the browser with command

`pnpm run story:dev`

You can also use [Histoire](https://histoire.dev/) to create stories for your components and test them in different scenarios.

## Versioning

This project follows [Semantic Versioning](https://semver.org/) but as the project is still pre-1.0. The code and the public exposed API should not be considered to be fixed and stable. Things can change at any time!

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT) - see [`LICENSE`](https://github.com/readyapi/readyapi/blob/main/LICENSE) for more details.

<div  align="center">

<br />

<br />

###### built with ❤︎ by the [ReadyAPI Team](https://github.com/readyapi) and [contributors](https://github.com/readyapi/readyapi/graphs/contributors).

</div>
