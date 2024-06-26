<template>
  
<div class="container">
    <div class="row">
        <div class="col">
            <img src="" alt="portfolio-picture" class="img-fluid">
        </div>

        <div class="col">
            <div id="details"></div>

        </div>
    </div>
</div>
</template>

<script setup>
import { computed, onMounted } from 'vue'
const jobTitle = computed(()=> this.$store.state.jobTitle)
onMounted(()=>{
    this.$store.dispatch('fetchJobTitle')
} )
</script>

<style>


</style>