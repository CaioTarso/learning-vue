<template>
  <TesteComponent msg="Aprendendo Vue.js"/>
  <VideoSection />
  <NewsSection :newsList="newsList" />
</template>

<script>
import TesteComponent from './components/teste.vue'
import VideoSection from './components/VideoSection.vue'
import NewsSection from './components/NewsSection.vue'

export default {
  name: 'App',
  components: {
    TesteComponent,
    VideoSection,
    NewsSection,


  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0;
  padding: 0;
  color: #2c3e50;
}
</style>
