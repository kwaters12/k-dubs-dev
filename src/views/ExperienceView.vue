<script lang="ts">
export enum Experience {
  Convertus = 'Convertus',
  BroadbandTV = 'BroadbandTV',
  StoryDriven = 'StoryDriven',
  Xeraflop = 'Xeraflop',
  iClinic = 'iClinic',
  Penny = 'Penny'
}
</script>
<script setup lang="ts">
type ExperienceItem = {
  id: Experience
  title: string
  company: string
  date: string
  description: string
  link?: string
  techStack: string[]
}
const experienceItems: ExperienceItem[] = [
  {
    id: Experience.Penny,
    title: 'Staff Engineer',
    company: 'Penny AI',
    date: '2020 - Present',
    description:
      'Work on the entire stack for Penny’s client facing web, iOS and Android apps. Including setting up our repositories, implementing and maintaining our localization solution, creating and maintaining CircleCI jobs, as well as delivering countless features, all while mentoring my teammates and collaborating with other teams.',
    link: 'https://trnd.io',
    techStack: ['Angular', 'Capacitor', 'Typescript', 'PostgreSQL', 'Django', 'AWS']
  },
  {
    id: Experience.iClinic,
    title: 'Software Engineer',
    company: 'iClinic Systems Inc.',
    date: '2018 - 2020',
    description:
      'Implemented scalable frontend solutions using Angular 7/8 with NgRx and Nrwl, creating a modular codebase that reduced development time for new features. Led the adoption of Git and NgRx, improving code quality and team collaboration while mentoring junior developers to enhance technical proficiency. Collaborated with UX/UI designers and backend teams to deliver responsive interfaces and optimize API designs, accelerating feature development and improving user satisfaction.',
    link: 'https://iclinicemr.com',
    techStack: ['Angular', 'Nrwl/Nx', 'Typescript', 'Java', 'Spring', 'Azure']
  },
  {
    id: Experience.Xeraflop,
    title: 'Software Engineer',
    company: 'Xeraflop Technologies',
    date: '2017 - 2018',
    description:
      'I worked on a team that built software for the legalized marijuana industry. I worked on a variety of projects, including a POS and online delivery software. We also did an ICO while I was there, which was... interesting and a great crash course into all things crypto.',
    techStack: ['React', 'Ruby on Rails', 'Angular.JS', 'Docker', 'Jenkins']
  },
  {
    id: Experience.StoryDriven,
    title: 'Web Developer',
    company: 'StoryDriven Inc.',
    date: '2017',
    description:
      'Implementing Codeship for deployments, and creating documentation to guide future web development projects. Create responsive emails for clients and update client websites.',
    techStack: ['Wordpress', 'Codeship', 'HTML', 'CSS', 'JavaScript']
  },
  {
    id: Experience.BroadbandTV,
    title: 'Frontend Developer',
    company: 'BroadbandTV Corp.',
    date: '2016 - 2017',
    description:
      'Developed the Catalyst for Chrome Extension to optimize YouTube videos for partners. Assisted in adopting modern development stacks using Docker, enhancing development efficiency and scalability.',
    link: 'https://bbtv.com/',
    techStack: ['React', 'Chrome Extensions', 'Docker', 'Jenkins', 'Python']
  },
  {
    id: Experience.Convertus,
    title: 'Web Development Specialist',
    company: 'Convertus',
    date: '2014 - 2015',
    description:
      'Assisted with UX/UI design for automotive websites and developed custom WordPress plugins, enhancing functionality and user experience. Implemented robust deployment and version control strategies, improving team efficiency and code quality.',
    link: 'https://convertus.com/',
    techStack: ['jQuery', 'JavaScript', 'PHP', 'MySQL', 'Docker', 'Wordpress']
  }
]

function clickHandler(link: string) {
  if (link) {
    window.open(link, '_blank') // Open the link in a new tab
  }
}
</script>
<template>
  <main>
    <div class="experience">
      <div
        v-for="item in experienceItems"
        class="experience-item"
        @click="clickHandler(item.link ?? '')"
        :id="item.id"
      >
        <p>
          <span class="date">{{ item.date }}</span>
          <strong> {{ item.title }} - {{ item.company }}</strong>
        </p>
        <p>{{ item.description }}</p>
        <ul>
          <li v-for="tech in item.techStack" :key="tech">{{ tech }}</li>
        </ul>
      </div>
    </div>
  </main>
</template>

<style>
.experience {
  padding: 1rem 0 0 0;

  strong {
    font-size: 1.2rem;
    font-weight: bold;
    padding-left: 1rem;
  }

  ul {
    list-style-type: none;
    padding: 0;
    li {
      display: inline;
      padding: 5px 1rem 8px 1rem;
      margin-right: 1rem;
      background-color: #1fff94;
      color: var(--color-background);
      border-radius: 15px;
    }
  }
}
.experience-item {
  p:first-of-type {
    margin-bottom: 0.5rem;
  }
  padding: 1rem 0 2rem 0;
}
</style>
