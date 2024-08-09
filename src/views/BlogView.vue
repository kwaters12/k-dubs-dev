<script setup lang="ts">
import { defineAsyncComponent, computed } from 'vue'
const BlogPosts = import.meta.glob('../assets/posts/*.md')
const components = computed(() => {
  return Object.keys(BlogPosts)
    .reverse()
    .map((path) => {
      return defineAsyncComponent(() => BlogPosts[path]().then((module: any) => module.default))
    })
})
</script>

<template>
  <main>
    <div class="blog">
      <component v-for="component in components" :is="component" />
    </div>
  </main>
</template>

<style>
.markdown-body {
  padding: 1.5rem 1rem 0 1rem;
  border-bottom: 1px solid var(--color-border);
  &:hover {
    background-color: rgba(75, 125, 136, 0.5);
  }
  h4 {
    font-weight: bold;
    margin: 1rem 0;
  }
  strong {
    font-weight: bold;
  }
  img {
    max-width: 100%;
  }
}
</style>
