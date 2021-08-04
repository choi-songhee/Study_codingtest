<template>
  <div id="app">
    <div class="inner">
      <div class="title">
        Snap photos and share like<br>
        never before
      </div>

      <profileCard />
    </div>
    <fullBleed />
  </div>
</template>

<script>
import profileCard from './components/profileCard.vue'
import fullBleed from './components/fullBleed.vue'

export default {
  name: 'App',
  components: {
    profileCard,
    fullBleed
  }
}
</script>

<style lang="scss">

body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #000;
}
.inner {
  padding: 120px 80px 0;
  .title {
    font-size: 48px;
    line-height: 1.5;
    letter-spacing: -0.72px;
    font-family: 'Exo2';
    font-weight: normal;
  }
}
</style>
