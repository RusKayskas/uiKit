<template>
  <div class="sidebar-wrapper">
    <div :class="['sidebar-overflow', {'sidebar-overflow--is-open': isOpen}]" @click="isOpen = false"/>
    <aside :class="['sidebar' , {'sidebar--is-open': isOpen}]">
      <button 
        class="sidebar__toggle" 
        :title="tooltypeSidebarText" 
        @click="openSidebar">
          <span class="sidebar__toggle-arror">
            &#5125;
          </span>
      </button>
      <router-link 
        v-for="link in links" 
        :key="link.name" 
        :to="link.href"
        class="sidebar__link"
      >
        {{ link.name }}
      </router-link>
    </aside>
  </div>
</template>

<script setup>
  import { ref, defineProps, defineEmits, computed } from 'vue';
  defineProps({
    links: {
      type: [],
      required: true,
    },
  });
  const emit = defineEmits(['open-sidebar']);
  const isOpen = ref(false);
  const openSidebar = () => {
    isOpen.value = !isOpen.value;
    emit('open-sidebar', isOpen.value);
  }
  const tooltypeSidebarText = computed(() => {
    return isOpen.value? 'Close sidebar' : 'Open Sidebar'; 
  });
</script>

<style lang="scss">
  .sidebar-overflow {
    position: fixed;
    width: 100%;
    height: 100%;
    left: -100%;
    transition: linear 0.1s;
    background-color: rgba(0, 0, 0, 0.4);
    &--is-open {
      left: 0;
    }
  }
  .sidebar {
    position: fixed;
    left: 0;
    top: 62px;
    height: 100%;
    width: 265px;
    padding: 20px 35px 20px 20px;
    transition: linear 0.2s;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.7);
    transform: translateX(-250px);
    z-index: 1;
    background-color: #fff;
    &--is-open {
      transform: translateX(0);
      .sidebar__toggle-arror {
        transform: rotate(180deg);
      }
    }
    &__toggle {
      position: fixed;
      right: 0;
      width: 16px;
      border: none;
      box-shadow: none;
      color: #fff;
      background: var(--primary-color);
      top: 0;
      height: 100%;
      z-index: 1;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
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