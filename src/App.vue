<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <LeftSidebar/>
    </div>
    <div class="column is-three-quarter">
      <TaskForm/>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import LeftSidebar from './components/LeftSidebar.vue'
import TaskForm from './components/TaskForm.vue'

export default defineComponent({
  name: 'App',
  components: {
    LeftSidebar,
    TaskForm
  }
});
</script>

<style>
</style>
