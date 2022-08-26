<template>
  <div class="Top">
    <span>Logo</span>
  </div>
</template>

<script>
export default {
  name: 'MyHeader'
}
</script>

<style lang="scss">
    @import '@/styles/vars.scss';
    .Top {
        background-color: $color_top;
        width: 100%;
        height: 50px;
    }

    span {
        color: white;
        line-height: 50px;
        margin-left: 20px;
    }
</style>