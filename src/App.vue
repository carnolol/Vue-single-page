<template>
  <div id="app">
   <Header/>
   <Hero />
  </div>
</template>

<script>
import Header from './components/Header'
import Hero from './components/Hero'

export default {
  name: 'App',
  components: {
    Header,
    Hero
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
