<template>
  <div id="homePage">
    <div id="button">
      <button @click="goToSearch">Recherche filtrée</button>
      <!-- <NuxtLink to="search"> 
      <UButton size="sm">Search</UButton>
      </NuxtLink> -->
    </div>
  <formation></formation>
  </div>
</template>
<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();
const goToSearch = () => {
  router.push({ path: '/search' });
};
</script>
<style scoped>
#button {
  display: flex;
  justify-content: center;
  margin-top: -22.5px;
}
button {
  background-color: #30063B;
  border: 1px solid white;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 10px;
  padding-bottom: 10px;
  border-radius: 15px;
  color: white;
}
</style>