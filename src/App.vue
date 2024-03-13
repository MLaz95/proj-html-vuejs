<script>
  import AppHeader from './components/AppHeader.vue'
  import AppMain from './components/AppMain.vue'
  import AppFooter from './components/AppFooter.vue'
  import loader from './components/loader.vue';


  export default{
    components: {
      AppHeader,
      AppMain,
      AppFooter,
      loader,
    }
  }

</script>

<template>
  <loader></loader>
  <AppHeader></AppHeader>
  <AppMain></AppMain>  
  <AppFooter></AppFooter>
</template>

<style lang="scss">
  @use './styles/general.scss' as *;

</style>
