<template>
  <div class="greetings">
    <a href="/">
      <h1 class="green">Kelly Waters</h1>
    </a>
    <h2>Senior Fullstack Developer</h2>
    <p>I love to build software, and have a high standard of quality.</p>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
