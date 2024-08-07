<script setup lang="ts">
type ExperienceItem = {
  title: string
  company: string
  date: string
  description: string
  techStack: string[]
}
const experienceItems: ExperienceItem[] = [
  {
    title: 'Software Developer',
    company: 'Direct-to-Consumer Sales Software',
    date: '2020 - Present',
    description:
      'I work on a team that builds software to help companies sell directly to consumers. I work on a variety of projects, including a new product that helps companies manage their inventory.',
    techStack: ['Vue.js', 'TypeScript', 'Node.js', 'PostgreSQL', 'Docker', 'Kubernetes']
  },
  {
    title: 'Software Developer',
    company: 'Medical Software Provider',
    date: '2018 - 2020',
    description:
      'I worked on a team that built software for medical professionals. I worked on a variety of projects, including a new product that helps doctors manage their patients.',
    techStack: ['React', 'JavaScript', 'Node.js', 'MongoDB', 'Docker', 'Kubernetes']
  },
  {
    title: 'Software Developer',
    company: 'Legalized Marijuana Startup',
    date: '2016 - 2018',
    description:
      'I worked on a team that built software for the legalized marijuana industry. I worked on a variety of projects, including a new product that helps marijuana growers manage their crops.',
    techStack: ['Angular', 'JavaScript', 'Node.js', 'MongoDB', 'Docker', 'Kubernetes']
  },
  {
    title: 'Software Developer',
    company: 'Marketing Agency',
    date: '2014 - 2016',
    description:
      'I worked on a team that built software for marketing agencies. I worked on a variety of projects, including a new product that helps marketing agencies manage their clients.',
    techStack: ['Ember.js', 'JavaScript', 'Ruby on Rails', 'PostgreSQL', 'Docker', 'Kubernetes']
  },
  {
    title: 'Software Developer',
    company: 'YouTube Creator Network Platform',
    date: '2012 - 2014',
    description:
      'I worked on a team that built software for YouTube creators. I worked on a variety of projects, including a new product that helps YouTube creators manage their videos.',
    techStack: ['Backbone.js', 'JavaScript', 'Ruby on Rails', 'PostgreSQL', 'Docker', 'Kubernetes']
  },
  {
    title: 'Software Developer',
    company: 'Car Dealership Website Maker',
    date: '2010 - 2012',
    description:
      'I worked on a team that built software for car dealerships. I worked on a variety of projects, including a new product that helps car dealerships manage their inventory.',
    techStack: ['jQuery', 'JavaScript', 'PHP', 'MySQL', 'Docker', 'Kubernetes']
  }
]
</script>
<template>
  <div class="experience">
    <div v-for="items in experienceItems">
      <h1>{{ items.title }}</h1>
      <h2>{{ items.company }}</h2>
      <h3>{{ items.date }}</h3>
      <p>{{ items.description }}</p>
      <ul>
        <li v-for="tech in items.techStack" :key="tech">{{ tech }}</li>
      </ul>
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
