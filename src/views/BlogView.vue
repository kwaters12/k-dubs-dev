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
  <component v-for="component in components" :is="component" />
</template>

<style>
.markdown-body {
  h1 {
    font-weight: bold;
    margin-bottom: 1rem;
  }
  strong {
    font-weight: bold;
  }
}
</style>
