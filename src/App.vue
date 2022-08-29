<template>
  <div id="app">
    <MyHeader :propsPassoGeneriASecondSon="generi" @funValoreFromSelect="funSelectMetodoPadre" />
    <AlbumList @spostoGeneriSonToDad="lavoroGeneriInDadFun" :propsPassoGeneriAFirstSon="generiSave"/>
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
  },
  data() {
    return {
      generiSave: '',
      generi: [],
    }
  },
  methods: {
    lavoroGeneriInDadFun(thisSalvoGeneri) {
      this.generi = thisSalvoGeneri;
    },
    funSelectMetodoPadre(valoreFromSelect) {
      this.generiSave = valoreFromSelect
    },
  }
}
</script>

<style lang="scss">
@import '@/styles/general.scss'

</style>
