<template>
  <div>
    <h1 class="title">Typography</h1>
    <h2 class="title title-lg">Typography</h2>
    <h2 class="title title-md">Typography</h2>
    <h2 class="title title-sm">Typography</h2>
  </div>
</template>

<script setup>

</script>

<style lang="scss">
  .title {
    font-size: 34px;
    color: var(--text-color);
    &-lg {
      font-size: 22px;
    }
    &-md {
      font-size: 17px;
    }
    &-sm {
      font-size: 15px;
    }
  }
</style>