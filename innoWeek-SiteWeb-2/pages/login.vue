<template>
    <div>
        <UInput color="gray" variant="outline" placeholder="Pseudo" v-model="pseudo" />
        <UInput color="gray" variant="outline" placeholder="Mot de passe" v-model="password" />
        <button @click="control">test</button>
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

const control = () => {
    allUser.value.forEach(element => {
        if(element.nickname == pseudo.value)
        {
            if(element.password == password.value)
            {
                console.log("réussi")
                return localStorage.setItem("userId", element.user_id)
            }
        }
    });
}

</script>