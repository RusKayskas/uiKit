<template>
  <div>
    <Header />
    <Sidebar :links="links" @open-sidebar="openSidebar" />
    <div class="container">
      <div :class="['content', {'content--is-open-sidebar': isOpenSidebar} ]">
        <router-view/>
      </div>
    </div>
  </div>
</template>
<script setup>
  import { ref } from 'vue';
  import Header from '@/components/layout/Header.vue';
  import Sidebar from '@/components/Ui/Sidebar.vue';

  const links = [
    {
      name: 'Typography',
      href: '/typography'
    },
    {
      name: 'Button',
      href: '/button'
    }
  ]
  const isOpenSidebar = ref(false);
  const openSidebar = (value) => {
    isOpenSidebar.value = value; 
  };
</script>
<style lang="scss">
  .content {
    transition: linear 0.2s;
    padding: 20px 16px;
    &--is-open-sidebar {
      margin-left: 256px;
    }
  }
</style>
