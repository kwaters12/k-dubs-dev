<script lang="ts">
enum Screens {
  Home = 'Home',
  Experience = 'Experience',
  Projects = 'Projects',
  Blog = 'Blog'
}
</script>

<script setup lang="ts">
import { ref } from 'vue'
import Greeting from './components/Greeting.vue'
import HomeView from './views/HomeView.vue'
import ExperienceView, { Experience } from './views/ExperienceView.vue'
import ProjectsView from './views/ProjectsView.vue'
import BlogView from './views/BlogView.vue'
const currentScreen = ref<Screens>(Screens.Home)
const homeRef = ref<HTMLElement | null>(null)
const experienceRef = ref<HTMLElement | null>(null)
const projectsRef = ref<HTMLElement | null>(null)
const blogRef = ref<HTMLElement | null>(null)
function scrollTo(view: any) {
  view.scrollIntoView({ behavior: 'smooth' })
}
function scrollToExperience(experience: Experience) {
  const elem = document.getElementById(experience)
  elem?.scrollIntoView({ behavior: 'smooth' })
}
function scrollNow() {
  const currentScrollPos = window.scrollY
  const homeTop = homeRef?.value?.offsetTop || 0
  const experienceTop = experienceRef?.value?.offsetTop || 0
  const projectsTop = projectsRef?.value?.offsetTop || 0
  const blogTop = blogRef?.value?.offsetTop || 0

  if (currentScrollPos >= blogTop - 5) {
    currentScreen.value = Screens.Blog
  } else if (currentScrollPos >= projectsTop - 5) {
    currentScreen.value = Screens.Projects
  } else if (currentScrollPos >= experienceTop - 5) {
    currentScreen.value = Screens.Experience
  } else {
    currentScreen.value = Screens.Home
  }

  // if (currentScrollPos < experienceTop) {
  //   currentScreen.value = Screens.Home
  // } else if (currentScrollPos >= experienceTop && currentScrollPos <= projectsTop) {
  //   currentScreen.value = Screens.Experience
  // } else if (currentScrollPos >= projectsTop && currentScrollPos <= blogTop) {
  //   currentScreen.value = Screens.Projects
  // } else {
  //   currentScreen.value = Screens.Blog
  // }
}
function handleScroll() {
  let doScoll: any

  window.onscroll = () => {
    clearTimeout(doScoll)
    doScoll = setTimeout(scrollNow, 100) // firing less scroll events
  }
  window.onresize = () => {
    clearTimeout(doScoll)
    doScoll = setTimeout(scrollNow, 100) // firing less scroll events
  }
}

handleScroll()
</script>

<template>
  <header>
    <div class="wrapper">
      <Greeting />

      <nav>
        <a :class="{ active: currentScreen === Screens.Home }" @click="scrollTo(homeRef)"
          >Profile</a
        >
        <a
          :class="{ active: currentScreen === Screens.Experience }"
          @click="scrollTo(experienceRef)"
          >Experience</a
        >
        <a :class="{ active: currentScreen === Screens.Projects }" @click="scrollTo(projectsRef)"
          >Projects</a
        >
        <a :class="{ active: currentScreen === Screens.Blog }" @click="scrollTo(blogRef)">Blog</a>
      </nav>

      <p class="resume">
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
    <div class="divider"></div>
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
  text-align: center;
  margin-top: 2rem;
  margin-bottom: 1rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
  text-decoration: underline;
}

nav a {
  font-size: 1em;
  cursor: pointer;
  display: inline-block;
  padding: 0 1rem 3px 1rem;
  &.active {
    color: var(--color-text);
    text-decoration: underline;
  }
}

nav a:first-of-type {
  border: 0;
}

.resume {
  text-align: center;
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
