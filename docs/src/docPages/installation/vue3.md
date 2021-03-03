# Vue.js 3 (Draft)

## toc

## Introduction
The following guide describes how to integrate tiptap with your [Vue](https://vuejs.org/) CLI project.

## Requirements
* [Node](https://nodejs.org/en/download/) installed on your machine
* [Vue CLI](https://cli.vuejs.org/) installed on your machine
* Experience with [Vue](https://vuejs.org/v2/guide/#Getting-Started)

## 1. Create a project (optional)
If you already have an existing Vue project, that’s fine too. Just skip this step and proceed with the next step.

For the sake of this guide, let’s start with a fresh Vue project called `tiptap-example`. The Vue CLI sets up everything we need, just select the default Vue 2 template.

```bash
# create a project
vue create tiptap-example

# change directory
cd tiptap-example
```

## 2. Install the dependencies
Okay, enough of the boring boilerplate work. Let’s finally install tiptap! For the following example you’ll need `@tiptap/core` (the actual editor) and the `@tiptap/vue-starter-kit` which has everything to get started quickly, for example a few default extensions and a basic Vue component.

```bash
# install with npm
npm install @tiptap/core @tiptap/vue-starter-kit

# install with Yarn
yarn add @tiptap/core @tiptap/vue-starter-kit
```

If you followed step 1 and 2, you can now start your project with `npm run dev` or `yarn dev`, and open [http://localhost:8080/](http://localhost:3000/) in your favorite browser. This might be different, if you’re working with an existing project.

## 3. Create a new component
To actually start using tiptap, you’ll need to add a new component to your app. Let’s call it `Tiptap` and put the following example code in `components/Tiptap.vue`.

This is the fastest way to get tiptap up and running with Vue. It will give you a very basic version of tiptap, without any buttons. No worries, you will be able to add more functionality soon.

```html
<template>
  <editor-content :editor="editor" />
</template>

<script>
import { Editor, EditorContent, defaultExtensions } from '@tiptap/vue-starter-kit'

export default {
  components: {
    EditorContent,
  },

  data() {
    return {
      editor: null,
    }
  },

  mounted() {
    this.editor = new Editor({
      content: '<p>I’m running tiptap with Vue.js. 🎉</p>',
      extensions: defaultExtensions(),
    })
  },

  beforeDestroy() {
    this.editor.destroy()
  },
}
</script>
```

## 4. Add it to your app
Now, let’s replace the content of `src/App.vue` with the following example code to use our new `Tiptap` component in our app.

```html
<template>
  <div id="app">
    <tiptap />
  </div>
</template>

<script>
import Tiptap from './components/Tiptap.vue'

export default {
  name: 'App',
  components: {
    Tiptap
  }
}
</script>
```

You should now see tiptap in your browser. You’ve successfully set up tiptap! Time to give yourself a pat on the back. Let’s start to configure your editor in the next step.

<!-- TODO: ## 5. Use v-model (optional)
You’re probably used to bind your data with `v-model` in forms, that’s also possible with tiptap. Here is a working example component, that you can integrate in your project:

<demo name="Guide/GettingStarted/VModel" /> -->