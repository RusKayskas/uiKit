<template>
  <aside :class="['sidebar' , {'sidebar--is-open': isOpen}]">
    <router-link 
      v-for="link in links" 
      :key="link.name" 
      :to="link.href"
      class="sidebar__link"
    >
      {{ link.name }}
    </router-link>
    <!-- <button @click="openSidebar">Open</button> -->
  </aside>
</template>

<script setup>
  import { ref, defineProps, defineEmits } from 'vue';
  defineProps({
    links: {
      type: [],
      required: true,
    },
  });
  const emit = defineEmits(['open-sidebar']);
  const isOpen = ref(true);
  const openSidebar = () => {
    isOpen.value = !isOpen.value;
    emit('open-sidebar', isOpen.value);
  }
</script>

<style lang="scss">
  .sidebar {
    position: fixed;
    left: 0;
    top: 62px;
    height: 100%;
    width: 262px;
    padding: 20px;
    transition: linear 0.2s;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.7);
    transform: translateX(-250px);
    background-color: #fff;
    &--is-open {
      transform: translateX(0);
    }
    &__link {
      display: block;
      border-radius: 12px;
      padding: 10px;
      border: 2px solid #fff;
      transition: linear 0.2s;
      font-weight: bold;
      margin-bottom: 10px;
      &:hover {
        border-color: var(--primary-color);
      }
    }
  }
</style>