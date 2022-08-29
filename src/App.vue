<template>
  <div id="app">
    <MyHeader />
    <AlbumList />
  </div>
</template>

<script>
import MyHeader from './components/MyHeader';
import AlbumList from './components/AlbumList';

export default {
  name: 'App',
  components: {
    MyHeader,
    AlbumList
  }
}
</script>

<style lang="scss">
@import '@/styles/general.scss'

</style>
