<script setup>
import formation from '~/data/formation.json'
import { useRouter } from 'vue-router';
import { onMounted } from 'vue';

const router = useRouter();
const items = ref([])

onMounted(() => {
    formation.formations.forEach((element) => {
        if(element.id < 4)
        {
            items.value.push(element)
        }
    })
})

function goToDetails(id) {
    router.push({ path: `/formation/${id}` });
}
</script>
<template>
    <div class="h-screen">
        <h1>Les formations les plus populaires</h1>
        <div class="cards">
            <div v-for="item in items" :key="item.id" class="card">
                <div v-if="item.premium">
                    <img id="crown" src="../public/crown.png">
                </div>
                <h2 :class="item.premium ? 'card-title-premium' : 'card-title'">{{ item.title }}</h2>
                <img :src="item.image" alt="logo formation" class="logo_formation">
                <div class="arrow" @click="goToDetails(item.id)">
                    <a>
                        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24">
                            <path fill="currentColor" d="M16.175 13H4v-2h12.175l-5.6-5.6L12 4l8 8l-8 8l-1.425-1.4z">
                            </path>
                        </svg>
                    </a>
                </div>
            </div>
        </div>
    </div>

</template>
<style scoped>
.arrow:hover {
    cursor: pointer;
}
#crown {
    height: 25px;
    margin-left: 173px;
    margin-top: -10px;
}
.card-title {
    margin-bottom: 33px;
    margin-top: 33px;
}
.card-title-premium {
    margin-bottom: 33px;
}
.arrow {
    padding: 10px;
    border-radius: 30px;
    background-color: #00CFC3;
    margin-left: 200px;
    margin-top: 50px;
}

h1 {
    font-size: 2em;
    color: white;
    margin-left: 5%;
}

.cards {
    display: flex;
    justify-content: space-around;
    margin-top: 5%;
    margin-bottom: 5%;
}

.card {
    background-color: #0C595E;
    border-radius: 15px;
    border: 1px solid black;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 250px;
    width: 200px;
}

.logo_formation {
    max-width: 200px;
    max-height: 100px;
    width: auto;
    background: none;
}

a {
    color: blue;
    text-decoration: underline;
}
</style>