<template>
    <div class="container">
        <LoadInProgress v-if="loadInProgress" />
        <div v-else class="row row-cols-4 g-3">
            <SingleAlbum  v-for="album in albumList" :key="album.id" :album="album" />
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import LoadInProgress from './LoadInProgress.vue';
import SingleAlbum from './SingleAlbum.vue';

export default {
    name: 'AlbumList',
    components: {
        SingleAlbum,
        LoadInProgress
    },
    data() {
        return {
            albumList: [],
            endpoint: 'https://flynn.boolean.careers/exercises/api/array/music',
            loadInProgress: true
        }
    },
    created() {
        this.getAlbum();
    },
    methods: {
        getAlbum() {
            let that = this;
            axios.get(this.endpoint)
            .then(function (response) {
                that.albumList = response.data;
                that.loadInProgress = false;
            })
            .catch(err => {
                console.log(err);
                that.loadInProgress = false;
            });
        }
    }
}

</script>

<style>

</style>