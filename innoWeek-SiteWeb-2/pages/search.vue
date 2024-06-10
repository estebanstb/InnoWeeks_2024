<template>
  <div class="size">
    <UContainer class="min-h-96 flex flex-col items-center w-full">
      <UProgress :value="progressBar" indicator class="w-full my-12" />
      <UCard class="flex-1 w-full" :ui="{
        background: 'bg-red',
        ring: 'ring-1 ring-gray-300 dark:ring-gray-700',
        header: { base: 'font-bold' },
      }">

        <template #header><p> Étape {{ step }} - {{ title[step - 1] }}</p></template>
        <!-- step 1 -->
        <USelectMenu v-if="step == 1" v-model="technology" :options="programLanguage" multiple
          placeholder="Selectionner les technologies maîtrisées" searchable searchable-placeholder="Search a technology..." />
        <!-- step 2 -->
        <div v-if="step == 2">
          <p>Prix minimum:</p>
          <UInput color="white" variant="outline" type="text" v-model="min" placeholder="minimum" />
          <p>Prix maximum:</p>
          <UInput color="white" variant="outline" type="text" v-model="max" placeholder="maximum" />
        </div>
        <!-- step 3 -->
        <USelectMenu v-if="step == 3" v-model="niveau" :options="niveauInformatique"
          placeholder="Votre niveau" />
        <!-- step 4 -->
        <div v-if="step == 4">
          <p>Temps de la formation</p>
          <UInput color="white" variant="outline" type="text" v-model="time" placeholder="Temps de la formation (mois)" />
        </div>
        <template #footer>
          <div class="flex justify-between">
            <UButton :disabled="step == 1" @click="previous" color="white">Previous</UButton>
            <UButton v-if="step != numberStep" @click="next">Next</UButton>
            <NuxtLink v-else :to="{ name: 'resultat', query: { technologie: technology, niveau: niveau, min: min, max:max, temps: time } }">
              <UButton>Finish</UButton>
            </NuxtLink>
          </div>
        </template>

      </UCard>
    </UContainer>
  </div>

</template>

<script setup>
import { ref } from 'vue';
import language from '~/data/language.json'

const programLanguage = language.programmingLanguages
const niveauInformatique = ["Débutant", "Débutant avancé", "Intermédiaire", "Intermédiaire avancé", "Expert", "Expert avancé"]

const technology = ref([])
const niveau = ref()
const min = ref()
const max = ref()
const time = ref()

const step = ref(1)
const numberStep = 4
const progressBar = computed(() => { return ((step.value - 1) / numberStep) * 100 })
const title = ["Technologie", "Prix", "Niveau des formations", "Temps de la formation"]

const next = () => {
  if (step.value < numberStep) {
    step.value++
  }
}
const previous = () => {
  if (step.value > 1) {
    step.value--
  }
}

</script>

<style scoped>
.size {
  height: 80vh;
}
</style>
