<template>
    <main class="container mt-5">
        <LoadInProgress v-if="loadInProgress" />
        <div class="d-flex flex-wrap">
            <MyDisc
                v-for="(element, index) in funFiltraggio"
                :key="index"
                :element="element"
            />
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import LoadInProgress from './LoadInProgress';
import MyDisc from './MyDisc';

export default {
    name: 'AlbumList',
    components: {
    MyDisc,
    LoadInProgress,
    },
    props: {
        propsPassoGeneriAFirstSon: String,
    },
    data() {
        return {
            salvoArrayAxios: [],
            loadInProgress: true,
            salvoGeneri: []
        }
    },
    computed: {
        funFiltraggio() {
            if (this.propsPassoGeneriAFirstSon === '') {
            return this.salvoArrayAxios
            } else {
                return this.salvoArrayAxios.filter((el) => {
                    return el.genre.includes(this.propsPassoGeneriAFirstSon);
                })
            }
        }   
    },
    created() {
        axios.get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((res) => {
            this.salvoArrayAxios = res.data.response;
            this.loadInProgress = false;
            this.salvoArrayAxios.forEach(el => {
                if (!this.salvoGeneri.includes(el.genre)) {
                    this.salvoGeneri.push(el.genre)
                }
            });
            this.$emit('spostoGeneriSonToDad', this.salvoGeneri)
        })
        .catch((err) => {
            console.log(err);
            this.loadInProgress = false;
        });
    }
}

</script>

<style>

</style>