<template>
  <UProgress :value="20" indicator class="w-1/5 " />
  <UContainer class="min-h-96 flex items-center">
    <UCard class="flex-1" :ui="{
    background: 'bg-red',
    ring: 'ring-1 ring-gray-300 dark:ring-gray-700',
    header: { base: 'font-bold' },
    }">

      <template #header> Étape {{ step }} </template>
      <USelectMenu v-if="step == 1" v-model="technology" :options="exemple" multiple placeholder="Select technologie" />
      <USelectMenu v-if="step == 2" v-model="technology2" :options="exemple" multiple placeholder="Select other" />
      <USelectMenu v-if="step == 3" v-model="technology3" :options="exemple" multiple placeholder="Select other 2" />
      <template #footer>
        <div class="flex justify-between">
          <UButton :disabled="step == 1" @click="previous" color="black">Previous</UButton>
          <UButton v-if="step != 3" @click="next">Next</UButton>
          <NuxtLink v-else :to="{name: 'resultat', query: {technology: technology}}">
            <UButton>Finish</UButton>
          </NuxtLink>
        </div>
      </template>

    </UCard>
  </UContainer>
</template>

<script setup>
import { ref } from 'vue';

const exemple = ['React', 'Vue', 'Angular', 'Express', 'Node', 'Mysql', 'MongoDB', 'PhpMyAdmin', 'Docker']

const technology  = ref([])
const technology2 = ref([])
const technology3 = ref([])
const step = ref(1)

const next = () => {
  if (step.value < 3)
  {
    step.value++
  }
}
const previous = () => {
  if (step.value > 1)
  {
    step.value--
  }
}
</script>