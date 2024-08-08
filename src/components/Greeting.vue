<template>
  <div class="greeting">
    <a href="/">
      <h1 class="blue">Kelly Waters</h1>
    </a>
    <h2>Senior Fullstack Developer</h2>
    <p>I love to build software and I love learning new things.</p>
  </div>
</template>

<style scoped>
a {
  margin: 0;
  padding: 0;
  color: var(--color-text);
}
a:hover,
a:active {
  background-color: transparent;
}
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greeting {
  text-align: center;
}

@media (min-width: 1024px) {
  .greeting {
    text-align: left;
  }
}
</style>
