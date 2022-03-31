<template>
  <div id="app">
    <Header/>
    <MainContent/>
  </div>
</template>

<script>
import Header from "./components/header/Header.vue"
import MainContent from "./components/main/MainContent.vue"

export default {
  name: 'App',
  components: {
    Header,
    MainContent
  },
}
</script>

<style lang="scss">

</style>
