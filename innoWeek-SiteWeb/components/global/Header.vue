<script setup>

</script>
<template>
    <nav id="header">
        <img src="../../public/ETML.png" alt="logo ETML" id="ETML">
        <div id="search">
            <img src="../../public/search.png" alt="logo loupe">
            <input type="text" placeholder="Rechercher..."
        </div>
    </nav>
</template>
<style scoped>
nav{
    background-image: linear-gradient(to right, #27F6E9 0%, #0F172A 44%);
    display: flex;
    align-items: center;
    justify-content: space-around;
    height: 80px;
    border-bottom-left-radius: 15px;
    border-bottom-right-radius: 15px;
}
#ETML {
    height: 50px;
}
#search {
    display: flex;
    border: solid 1px white;
    border-radius: 15px;
    height: 40px;
}
input {
    background: none;
}
</style>