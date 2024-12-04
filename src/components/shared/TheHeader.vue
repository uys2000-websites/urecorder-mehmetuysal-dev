<template>
  <header class="px-4 pt-4 sticky top-0 z-10 flex-shrink-0">
    <div class="bg-neutral text-neutral-content flex justify-between items-center p-4 rounded-box">
      <RouterLink class="btn btn-sm btn-ghost" :to="{ name: 'HomeView' }">
        URecorder
      </RouterLink>
      <div class="flex gap-2">
        <a class="btn btn-sm btn-ghost" href="https://app.urecorder.mehmetuysal.dev">
          Web App
        </a>
        <RouterLink class="btn btn-sm btn-ghost" :to="{ name: 'AboutView' }">
          About
        </RouterLink>
        <ThemeBtn />
      </div>
    </div>
  </header>
</template>

<script lang="ts">
import { RouterLink } from 'vue-router';
import Dropdown from '../daisy/Dropdown.vue';
import DropdownContent from '../daisy/DropdownContent.vue';
import ThemeBtn from '../daisy/ThemeBtn.vue';

export default {
  components: { RouterLink, Dropdown, DropdownContent, ThemeBtn },

}
</script>