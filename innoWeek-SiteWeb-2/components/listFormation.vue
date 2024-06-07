<script setup>
import formation from '~/data/formation.json'
const items = ref(formation.formations)
</script>

<template>
    <div>
        <h2 class="font-bold text-6xl">Top formations</h2>
        <UCard v-for="item in items" :key="item.id" class="black-bg">
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
                    <svg v-if="item.premium" class="justify-items-start" xmlns="http://www.w3.org/2000/svg" fill="red" width="3em" height="3em"
                        viewBox="0 0 48 48">
                        <defs>
                            <mask id="ipTCrownThree0">
                                <g fill="#FFF" stroke="#FFF" stroke-width="4">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M13 42h22l6-21l-10 5l-7-14l-7 14l-10-5z">
                                    </path>
                                    <circle cx="7" cy="18" r="3"></circle>
                                    <circle cx="24" cy="9" r="3"></circle>
                                    <circle cx="41" cy="18" r="3"></circle>
                                </g>
                            </mask>
                        </defs>
                        <path fill="currentColor" d="M0 0h48v48H0z" mask="url(#ipTCrownThree0)"></path>
                    </svg>
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
.black-bg {
    background-color: #151967;
    margin-bottom: 75px;
    margin-top: 50px;
}

.placement {
    align-self: flex-end;
    justify-self: flex-end;
    margin-top: auto; /* Ajouté pour pousser le bouton vers le bas */
}

.flex-collum {
    display: flex;
    flex-direction: column;
    justify-content: space-between; /* Ajouté pour répartir l'espace */
    height: 100%; /* Ajouté pour s'assurer que l'élément prend toute la hauteur */
}
</style>
