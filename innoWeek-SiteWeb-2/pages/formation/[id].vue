<script setup>
import formation from '~/data/formation.json'

const route = useRoute();
const items = ref(formation.formations)
let data = ref(null)
let idRoute = route.params.id
const token = ref()

items.value.forEach(element => {
    if (element.id == idRoute) {
        data = element;
    }
});

function goToWebSite(url) {
    window.open(url, '_blank');
}

onMounted(() => {
    token.value = localStorage.getItem('userId')
})
</script>
<template>
    <div>
        <div>
            <div class="head">
                <div v-if="data.deprecated" class="warning">
                    <h2><span class="warning_message">ATTENTION, la formation n'est plus à jour</span></h2>
                </div>
                <div class="card">
                    <div class="main_info">
                        <div v-if="data.premium" id="crown_container">
                            <img id="crown" src="../../public/crown.png">
                        </div>

                        <img id="logo" :src="data.image" alt="logo de la formation">
                        <h1>{{ data.title }}</h1>
                        <p id="description">{{ data.description }}</p>
                        <div class="information">
                            <p>{{ data.monthDuration }}mois</p>
                            <p>{{ data.euroPrice }}€</p>
                            <p>{{ data.difficulty }}</p>
                        </div>

                        <div class="certificate">
                            <p v-if="data.recognisedCertificate">Certificat reconnu</p>
                            <p v-else>certificat non reconnu</p>
                        </div>

                        <button class="button" type="button" @click="goToWebSite(data.url)">Site</button>
                    </div>

                    <div class="long_information">
                        <div class="languageUsed">
                            <p>Langages utilisés : </p>
                            <ul>
                                <li v-for="languageUsed in data.programmingLanguageUsed">{{ languageUsed }}</li>
                            </ul>
                        </div>

                        <div class="competence">
                            <p>Compétences acquises :</p>
                            <ul>
                                <li v-for="acquiredCompetence in data.acquiredCompetence">{{ acquiredCompetence }}</li>
                            </ul>
                        </div>

                        <div class="require">
                            <p>Prérequis :</p>
                            <ul v-if="data.languageRequirements.length > 0">
                                <li v-for="requirement in data.languageRequirements">{{ requirement }}</li>
                            </ul>
                            <p v-else>Aucun</p>
                        </div>
                    </div>

                    <div v-if="data.modules.length > 0" class="segmentation">
                        <h2>Différentes parties de la formation</h2>
                        <div v-for="part in data.modules" class="part">
                            <h3>{{ part.title }} - {{ part.module_id }}</h3>
                            <p>{{ part.description }}</p>
                        </div>
                    </div>

                    <div v-if="data.instructors.length > 0" class="instructors">
                        <div v-for="instructor in data.instructors" class="instructor">
                            <p>{{ instructor.fullName }}</p>
                            <p><a :href="`mailto:${instructor.mail}`">{{ instructor.mail }}</a></p>
                        </div>
                    </div>
                    <div class="flex justify-center">

                        <NuxtLink v-if="data.premium && token == null" to="/login">
                            <UButton class="button">
                                Connectez vous pour faire la formation
                            </UButton>
                        </NuxtLink>
                        <UButton class="button" v-else>
                            Faire la formation
                        </UButton>
                    </div>

                </div>
            </div>

        </div>
    </div>
</template>
<style scoped>
.button:hover {
    background-color: #00CFC3;
}

.instructor {
    padding-bottom: 20px;
}

.warning {
    width: 100%;
    background-color: #FF0000;
}

@keyframes defilement-rtl {
    0% {
        transform: translate3d(100%, 0, 0);
        /* position final à droite */

    }

    100% {
        transform: translate3d(-50%, 0, 0);
        /* position initiale à gauche */

    }
}

.warning>h2 {
    animation: defilement-rtl 15s infinite linear;
}

.part {
    margin-top: 20px;
}

h1 {
    margin-left: 15px;
}

.instructors {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    margin-left: 15px;
    padding-top: 20px;
}

.segmentation {
    margin-left: 15px;
    padding-top: 10px;
}

.certificate {
    padding-bottom: 20px;
}

button {
    background-color: #0E0F33;
    padding: 5px 15px;
    border-radius: 5px;
    border: 1px solid black;
}

li {
    list-style-type: disc;
}

.competence {
    grid-column: 2;
    grid-row: 1/3;
}

.long_information {
    display: grid;
    grid-template: 1fr 1fr / 1fr 1fr;
}

.require {
    grid-column: 1;
    grid-row: 2;
    margin-left: 30px;
    margin-top: 10px;
}

.languageUsed {
    margin-left: 30px;
    grid-column: 1;
    grid-row: 1;
}

.main_info {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-bottom: 30px;
}

#crown_container {
    width: 50%;
    position: relative;
    margin-left: 140%;
    margin-top: -20px;
}

#crown {
    height: 40px;
}

.information {
    display: flex;
    justify-content: space-between;
    width: 90%;
    margin-bottom: 10px;
}

.head {
    display: flex;
    flex-direction: column;
    align-items: center;
    overflow: hidden;
}

#description {
    width: 80%;
    margin-bottom: 10px;
}

.card:last-child {
    padding-bottom: 20px;
}

.card {
    margin-top: 50px;
    background-color: #0C595E;
    width: 50%;
    min-width: 320px;
    border-radius: 20px;
    margin-bottom: 50px;
}

a {
    text-decoration: underline;
}

h3 {
    font-size: 1.17em;
}

h2 {
    font-size: 1.5em;
}

p,
h1,
li,
button,
h2,
h3 {
    color: white;
}

#logo {
    max-height: 350px;
    min-height: 300px;
    padding-top: 20px;
}

h1 {
    font-size: 2em;
}
</style>