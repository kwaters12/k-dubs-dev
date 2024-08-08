<script setup lang="ts">
import { Experience } from './ExperienceView.vue'
</script>

<template>
  <main>
    <div class="profile">
      <p>
        Ever since the days of Windows 3.1 and DOS, I have been obsessed for how computers work. As
        a kid, software and games seemed almost magic to me. Since then I’ve been working to
        demystify. Starting my career in game development, I’ve been peeling back the onion of
        software development since, having worked at a
        <a @click="$emit('scrollToExperience', Experience.Convertus)">
          car dealership website maker</a
        >,
        <a @click="$emit('scrollToExperience', Experience.BroadbandTV)"
          >YouTube creator network platform</a
        >, <a @click="$emit('scrollToExperience', Experience.StoryDriven)">marketing agency</a>,
        <a @click="$emit('scrollToExperience', Experience.Xeraflop)">legalized marijuana startup</a
        >,
        <a @click="$emit('scrollToExperience', Experience.iClinic)">medical software provider</a>,
        and most recently on
        <a @click="$emit('scrollToExperience', Experience.Penny)"
          >direct-to-consumer sales software</a
        >.
      </p>
      <p>
        I've been lucky to have done a ton of different things at this point in my career, and I am
        still learning. I love making things and solving hard problems.
      </p>
      <p>
        As a proud father, I try and take time away from the computer, enjoying this beautiful
        country I live in 🇨🇦. Activities include swimming, hiking, biking, picnicking, playing at
        the playground, and even the odd video game session.
      </p>
    </div>
  </main>
</template>

<style>
p {
  margin-bottom: 1.5rem;
  font-weight: lighter;
}
li {
  font-weight: lighter;
}
.profile {
  a {
    color: var(--color-text);
    font-weight: bold;
    cursor: pointer;
    &:hover {
      color: #1fff94;
    }
  }
}
</style>
