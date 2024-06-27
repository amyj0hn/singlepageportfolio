<template>
  <div>
    <Card v-for="project in projects" :key="project.id">
        <template #cardHeader>
<img src="" alt="">
        </template>

        <template #cardBody>


        </template>
    </Card>
  </div>
</template>

<script setup>
import Card from '@/components/Card.vue'

import { computed, onMounted, ref } from "vue";
import { useStore } from "vuex";
const store = useStore();
const cnt = ref(-1);
//This line of code accesses your data as object
const projects = computed(() => store.state.projects);
function repeat() {
  try {
    if (cnt.value == projects.value?.length) cnt.value = 0;
    store.value = projects.value?.at(cnt.value)?.projects;
    setTimeout(repeat, 2000);
    cnt.value++;
  } catch (e) {
    //
  }
}

onMounted(() => {
  store.dispatch("fetchProjects");
  repeat();
});
</script>

<style>

</style>