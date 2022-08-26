<template>
  <div id="app">
    <MyHeader/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader';

export default {
  name: 'App',
  components: {
    MyHeader,

  }
}
</script>

<style lang="scss">
@import '@/styles/general.scss'

</style>
