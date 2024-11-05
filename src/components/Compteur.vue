<script setup>
import {ref} from 'vue'
import Compteur from "@/components/Compteur.vue";
const monCompteur = ref(0)
</script>

<template>
<button @click="monCompteur++">{{monCompteur}}</button>
</template>

<style scoped>

</style>