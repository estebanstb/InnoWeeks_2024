<template>
    <div class="height flex items-center">
        <div class="login-container">
            <h1>Connexion</h1>
            <UInput color="gray" variant="outline" placeholder="Pseudo" v-model="pseudo" class="input" />
            <UInput color="gray" variant="outline" placeholder="Mot de passe" v-model="password" class="input" />
            <button @click="control">Se connecter</button>
        </div>
    </div>

</template> 

<script setup>
import { onMounted, ref } from 'vue';
import users from '~/data/users.json'
const allUser = ref()

onMounted(() => {
    allUser.value = users.users
})

const pseudo = ref()
const password = ref()
const isConnect = ref(false)

const control = () => {
    allUser.value.forEach(element => {
        if(element.nickname == pseudo.value)
        {
            if(element.password == password.value)
            {
                alert("Connexion réussi")
                isConnect.value = true
                return localStorage.setItem("userId", element.user_id)
            }
        }
    });
    if(!isConnect.value)
    {
        alert("Utilisateur ou mot de passe incorrect")
    }
}

</script>
<style scoped>
.login-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    background-color: #0C595E;
}

.login-container UInput {
    width: 100%;
    margin-bottom: 15px;
    padding: 10px;
    border-radius: 5px;
}

button {
    color: white;
    background-color: #0E0F33;
    padding: 10px 20px;
    border: 1px solid black;
    border-radius: 15px;
    margin-top: 15px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

button:hover {
    background-color: #094749;
}
.input {
    background-color: #094749;
    margin-top: 10px
}

.height{
    height: 80vh;
}
</style>