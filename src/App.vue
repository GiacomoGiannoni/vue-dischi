<template>
  <div id="app">
    <MyHeader :propsPassoGeneriASecondSon="generi" @funValoreFromSelect="funSelectMetodoPadre" />
    <AlbumList @spostoGeneriSonToDad="lavoroGeneriInDadFun" :propsPassoGeneriAFirstSon="valoreSalvatoInPadre" />
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
      valoreSalvatoInPadre: '',
      generi: []
    }
  },
  methods: {
    lavoroGeneriInDadFun(thisSalvoGeneri) {
      this.generi = thisSalvoGeneri;
    },
    funSelectMetodoPadre(valoreFromSelect) {
      this.valoreSalvatoInPadre = valoreFromSelect
    }
  }
}
</script>

<style lang="scss">
@import '@/styles/general.scss'

</style>
