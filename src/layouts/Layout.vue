<template>
  <div class="h-screen w-full bg-base-300 relative flex flex-col flex-nowrap overflow-hidden">
    <TheHeader />
    <div class="h-full w-full relative flex flex-col flex-shrink" :class="{ 'overflow-hidden': appStore.overflow }">
      <router-view v-slot="{ Component, route }">
        <transition name="page">
          <component :is="Component" :key="route.path" />
        </transition>
      </router-view>
    </div>
  </div>
</template>

<script lang="ts">
import TheHeader from '@/components/shared/TheHeader.vue';
import { useAppStore } from '@/stores/app';
import { RouterView } from 'vue-router'
export default {
  components: {
    TheHeader,
    RouterView
  },
  data() {
    return {
      appStore: useAppStore()
    }
  },
  mounted() {
    const adScript = document.createElement('script')
    adScript.innerHTML = `aclib.runAutoTag({
        zoneId: 'rmvblyfrsm',
    });`
    document.body.appendChild(adScript)
  }
}
declare global {
  var aclib: {
    runAutoTag: (...args: any) => Promise<any>
    runBanner: (...args: any) => Promise<any>
  };
}
</script>

<style>
.page-enter-active,
.page-leave-active {
  position: fixed;
  transition: 0.5s ease;
}

.page-enter-from {
  transform: translateY(100vh);
  opacity: 0;
}

.page-leave-to {
  transform: translateY(-100vh);
  opacity: 0;
}
</style>