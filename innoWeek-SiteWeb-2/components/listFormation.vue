<script setup>
const props = defineProps({
    formation: Array,
    title: String
})

</script>

<template>
    <div>
        <h2 class="font-bold text-6xl">{{ title }}</h2>
        <UCard v-for="item in formation" :key="item.id" class="black-bg">
            <div class="flex justify-between">
                <div class="flex">
                    <img :src="item.image" class="w-28 mr-8" alt="">
                    <div>
                        <p class="font-bold">{{ item.title }}</p>
                        <p class="font-thin">{{ item.description }}</p>
                        <div class="flex">
                            <p class="font-thin mr-20 mt-10">{{ item.difficulty }}</p>
                            <p class="font-thin mt-10">{{ item.monthDuration }} mois</p>
                        </div>
                    </div>
                </div>
                <div class="flex flex-collum">
                    <div class="crown-container">
                        <img v-if="item.premium" src="../public/crown.png" alt="premium" class="crown">
                    </div>

                    <NuxtLink class="placement" :to="{ name: 'formation-id', params: { id: item.id } }">
                        <UButton class="blue-color-bg">
                            Voir
                        </UButton>
                    </NuxtLink>
                </div>
            </div>
        </UCard>
    </div>

</template>

<style scoped>
.crown-container {

}

.crown {
    height: 30px;
    width: auto
}

.black-bg {
    background-color: #151967;
    margin-bottom: 75px;
    margin-top: 50px;
}

.placement {
    align-self: flex-end;
    justify-self: flex-end;
    margin-top: auto;
    /* Ajouté pour pousser le bouton vers le bas */
}

.flex-collum {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    /* Ajouté pour répartir l'espace */
    height: 100%;
    /* Ajouté pour s'assurer que l'élément prend toute la hauteur */
}
</style>
