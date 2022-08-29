<template>
    <main class="container mt-5">
        <LoadInProgress v-if="loadInProgress" />
        <div class="d-flex flex-wrap">
            <MyDisc
                v-for="(discItem, index) in discs"
                :key="index"
                :disc="discItem"
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
    data() {
        return {
            discs: [],
            loadInProgress: true
        }
    },
    created() {
        axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((res) => {
                this.discs = res.data.response;
                this.loadInProgress = false;
            })
            .catch((err) => {
                console.log(err);
                this.loadInProgress = false;
            });
    },
}

</script>

<style>

</style>