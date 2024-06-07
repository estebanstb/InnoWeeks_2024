<template>
  <div>
    <Welcome />
    <ListFormation v-if="list.length" :title="'Top des formations'" :formation="list" />
  </div>

</template>

<script setup>
import ListFormation from '~/components/listFormation.vue'
import formation from '~/data/formation.json'
const list = ref([])

onMounted(() => {
  formation.formations.forEach((element) => {
    if (element.id < 4) {
      list.value.push(element)
    }
  })
})
</script>