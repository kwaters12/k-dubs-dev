<script setup lang="ts">
import { defineAsyncComponent, computed } from 'vue'
const BlogPosts = import.meta.glob('../assets/posts/*.md')
const components = computed(() => {
  return Object.keys(BlogPosts).map((path) => {
    return defineAsyncComponent(() => BlogPosts[path]().then((module: any) => module.default))
  })
})
</script>

<template>
  <main>
    <component v-for="component in components" :is="component" />
  </main>
</template>

<style>
.markdown-body {
  h4 {
    font-weight: bold;
    margin: 1rem 0;
  }
  strong {
    font-weight: bold;
  }
}
</style>
