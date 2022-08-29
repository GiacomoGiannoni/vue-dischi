<template>
    <div class="disc p-3 text-center">
         <div class="p-3">
             <img :src="autore.poster" :alt="autore.name" class="img-fluid mb-3"/>
             <p class="title text-uppercase fw-bold">{{autore.title}}</p>
             <p class="author lead mb-0">{{autore.author}}</p>
             <p class="year">{{autore.year}}</p>
         </div>
   </div>
</template>
 
 <script>
 export default {
     name: 'MyAuthor',
     props: {
         autore: Object,
     }
 }
 </script>
 
 <style lang="scss" scoped>
     @import '@/styles/vars.scss';
     .disc {
         flex-basis: calc(100% / 5);
 
         div {
             background-color: $color_card;
             height: 100%;
         }
 
         .title {
             color:$color_text1;
         }
 
         .author, .year {
             color: $color_text2;
         }
     }
 </style>