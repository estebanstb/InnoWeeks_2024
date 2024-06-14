<script setup>
import { useRoute } from 'vue-router';
import { onMounted } from 'vue';
import formation from '~/data/formation.json'
const items = ref(formation.formations)
const formValid = ref([])

const hasAllDemandedLanguages = (demanded, mastered) => {
  return demanded.every(language => mastered.includes(language));
};

const isNotNullOrEmpty = (value) => {
    if(value == undefined || value == '')
    {
        return false
    }
    return true
}

onMounted(() => {
    items.value.forEach((element) => {
        if(isNotNullOrEmpty(route.query.technologie) && !hasAllDemandedLanguages(element.languageRequirements, route.query.technologie))
        {
            return false
        }
        if(isNotNullOrEmpty(route.query.max) && !(element.euroPrice <= route.query.max))
        {
            return false
        }
        if(isNotNullOrEmpty(route.query.min) && !(element.euroPrice >= route.query.min))
        {
            return false
        }
        if(isNotNullOrEmpty(route.query.niveau) && !(element.difficulty == route.query.niveau))
        {
            return false 
        }
        if(isNotNullOrEmpty(route.query.temps) && !(element.monthDuration <= route.query.temps))
        {
            return false 
        }
        formValid.value.push(element)
    })
})
const route = useRoute()
</script>

<template>
    <ListFormation v-if="formValid.length" :title="'Formation proposée'" :formation="formValid"/>
    <div v-else class="height">
        <p>Aucune formation ne correspond à vos critères</p>
    </div>
</template>

<style scoped>
    .height{
        height: 80vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>