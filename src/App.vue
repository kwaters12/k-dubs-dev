<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import Greeting from './components/Greeting.vue'
import HomeView from './views/HomeView.vue'
import ExperienceView, { Experience } from './views/ExperienceView.vue'
import ProjectsView from './views/ProjectsView.vue'
import BlogView from './views/BlogView.vue'
const homeRef = ref<HTMLElement | null>(null)
const experienceRef = ref<HTMLElement | null>(null)
const projectsRef = ref<HTMLElement | null>(null)
const blogRef = ref<HTMLElement | null>(null)
function scrollTo(view: Ref<HTMLElement | null>) {
  view.scrollIntoView({ behavior: 'smooth' })
}
function scrollToExperience(experience: Experience) {
  const elem = document.getElementById(experience)
  elem?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <header>
    <div class="wrapper">
      <Greeting />

      <nav>
        <a @click="scrollTo(homeRef)">Profile</a>
        <a @click="scrollTo(experienceRef)">Experience</a>
        <a @click="scrollTo(projectsRef)">Projects</a>
        <a @click="scrollTo(blogRef)">Blog</a>
      </nav>

      <p>
        Click here to download my latest
        <a href="/resume.pdf" target="_blank" rel="noopener noreferrer"> Resume </a>
      </p>
    </div>
  </header>

  <!-- <RouterView /> -->
  <div class="content">
    <section ref="homeRef">
      <HomeView @scrollToExperience="(experience) => scrollToExperience(experience)" />
    </section>
    <div class="divider"></div>
    <section ref="experienceRef">
      <ExperienceView />
    </section>
    <div class="divider"></div>
    <section ref="projectsRef">
      <ProjectsView />
    </section>
    <div class="divider"></div>
    <section ref="blogRef">
      <BlogView />
    </section>
    <section ref="footerRef">
      <footer>
        <p>
          Made in {{ new Date().getFullYear() }} with VueJS and Vite. Hosted on Vercel. Source code
          available on <a href="https://github.com/kwaters12/k-dubs-dev">GitHub</a>.
        </p>
      </footer>
    </section>
  </div>
</template>

<style scoped>
template {
  display: flex;
  flex-direction: row;
}
section {
  padding: 2rem 0;
}
header {
  line-height: 1.5;
  background-color: var(--color-background);
  max-height: 100vh;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
  margin-bottom: 1rem;
  a {
    cursor: pointer;
  }
}

nav a.router-link-exact-active {
  color: var(--color-text);
  text-decoration: underline;
}

nav a {
  display: inline-block;
  padding: 0 1rem 3px 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    position: sticky;
    top: 0;
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
    background-color: transparent;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }

  .content {
    padding: 245px 0 2rem;
  }
}

.divider {
  height: 1px;
  background-color: var(--color-border);
  margin: 2rem 0;
}
</style>
