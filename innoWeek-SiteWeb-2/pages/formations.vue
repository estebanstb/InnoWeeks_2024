<script setup>
import ListFormation from '~/components/listFormation.vue'
import formation from '~/data/formation.json'

const list = ref([])

onMounted(() => {
  formation.formations.forEach((element) => {
    if (element.id > 0) {
      list.value.push(element)
    }
  })
})

</script>
<template>
     <div id="">
        <h1>Nos propositions de formations</h1>
        <ListFormation v-if="list.length" :formation="list" />
     </div>
</template>
<style scoped> /* scoped défini que le style css n'a d'effet que sur ce fichier */
   h1 {
      font-size: 40px;
      display: flex;
      flex-direction: row;
      justify-content: center;

      border: 8px;
      border-color: white;
      border-style: solid;
      border-radius: 100px;
   }
</style>