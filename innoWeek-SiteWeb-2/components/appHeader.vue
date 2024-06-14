<template>
    <div class="p-2 flex justify-between px-28">
        <NuxtLink to="/">
            <p class="font-bold text-4xl flex items-center">ITFORM</p>
        </NuxtLink>
        <ul class="flex items-center">
            <li>
                <NuxtLink to="/">
                    Accueil
                </NuxtLink>
            </li>
            <li>
                <NuxtLink to="/formations">
                    Formations
                </NuxtLink>
            </li>
            <li>
                <NuxtLink to="/search">
                    Recherche personnalisé
                </NuxtLink>
            </li>
            <li>
                <NuxtLink to="/login">
                    Compte
                </NuxtLink>
            </li>
        </ul>
    </div>
</template>

<style scoped>
ul>li {
    font-weight: lighter;
    margin-left: 50px;
}
</style>