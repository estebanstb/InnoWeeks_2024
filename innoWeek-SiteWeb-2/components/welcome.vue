<template>
    <UContainer class="flex justify-center items-center h-screen flex-col">
        <h1 class="font-bold text-8xl">Les formations</h1>
        <h1 class="font-bold text-8xl text-teal-400">Pour votre avenir</h1>
        <p>Rechercher la formation pour votre avenir</p>
        <NuxtLink class="margin" to="search">
            <UButton class="blue-color-bg">
                Search
            </UButton>
        </NuxtLink>
    </UContainer>
</template>

<style scoped>
.blue-color-bg{
    background-color:#00CFC3;
    color: white;
    font-weight: bold;
    letter-spacing:2px;
}
.blue-color-bg:hover{
    background-color:#049790;
}
.margin{
    margin-top: 100px
}
</style>