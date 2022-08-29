<template>
  <div class="Top">
    <span class="">Logo</span>
    <div>
      <select class="p-2 select" v-model="valoreFromSelect" @change="$emit('funValoreFromSelect', valoreFromSelect)" name="select_genre" id="select_genre">
        <option value="" disabled selected>Scegli un genere</option>
        <option v-for="(element, index) in propsPassoGeneriASecondSon" :key="index" :value="element">{{element}}</option>
      </select>
      <select class="p-2 select" v-model="valoreSelect" @change="$emit('ValoreFromSelect', valoreSelect)" name="select_author" id="select_author">
        <option value="" disabled selected>Scegli un autore</option>
        <option v-for="(autore, index) in propsPassoAutoriASecondSon" :key="index" :value="autore">{{autore}}</option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MyHeader',
  props: {
      propsPassoGeneriASecondSon: Array,
      propsPassoAutoriASecondSon: Array,
    },
    data() {
        return {
            valoreFromSelect: '',
            valoreSelect: '',
        }
    }
}
  
</script>

<style lang="scss">
    @import '@/styles/vars.scss';
    .Top {
        background-color: $color_top;
        width: 100%;
        height: 50px;
        display: flex;
        justify-content: space-between;
    }

    span {
        color: white;
        line-height: 50px;
        margin-left: 20px;
    }

    .select {
      margin: 5px 20px 5px 0px;
    }
</style>