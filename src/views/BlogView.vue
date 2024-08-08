<script setup>
import { defineComponent, defineAsyncComponent, computed } from 'vue'
const BlogPosts = import.meta.glob('../assets/posts/*.md')
const components = computed(() => {
  return Object.keys(BlogPosts).map((path) => {
    const name = path.replace('../assets/posts/', '').replace('.md', '')
    return defineAsyncComponent(() => BlogPosts[path]().then((module) => module.default))
  })
})
</script>

<template>
  <component v-for="component in components" :is="component" />
</template>
