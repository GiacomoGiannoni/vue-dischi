<template>
    <main class="container mt-5">
        <LoadInProgress v-if="loadInProgress" />
        <div class="d-flex flex-wrap">
            <MyDisc v-for="(element, index) in funFiltraggio" :key="index" :element="element"/>
            <MyAuthor v-for="(autore, index) in funAutori" :key="'aut' + index" :autore="autore" />
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import LoadInProgress from './LoadInProgress';
import MyDisc from './MyDisc';
import MyAuthor from './MyAuthor';


export default {
    name: 'AlbumList',
    components: {
        MyDisc,
        LoadInProgress,
        MyAuthor
},
    props: {
        propsPassoGeneriAFirstSon: String,
        propsPassoAutoriAFirstSon: String,
    },
    data() {
        return {
            loadInProgress: true,
            salvoArrayAxios: [],
            salvoGeneri: [],
            salvoAxios: [],
            salvoAutori: [],
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
        },
        funAutori() {
            if (this.propsPassoAutoriAFirstSon === '') {
            return this.salvoAxios
            } else {
                return this.salvoAxios.filter((el) => {
                    return el.author.includes(this.propsPassoAutoriAFirstSon);
                })
            }
        }   
    },
    created() {
        axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((res) => {
            this.salvoArrayAxios = res.data.response;
            this.loadInProgress = false;
            this.salvoArrayAxios.forEach(el => {
                if (!this.salvoGeneri.includes(el.genre)) {
                    this.salvoGeneri.push(el.genre)
                }
            });
            this.$emit('spostoGeneriSonToDad', this.salvoGeneri)
        })
        axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((res) => {
            this.salvoAxios = res.data.response;
            this.salvoAxios.forEach(el => {
                if (!this.salvoAutori.includes(el.author)) {
                    this.salvoAutori.push(el.author)
                }
            });
            this.$emit('spostoAutoriSonToDad', this.salvoAutori)
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