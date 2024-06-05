<script setup>
    import formation from '~/data/formation.json'
    const items = ref(formation.formations)
    console.log(items.value)
</script>

<template>
    <div class="flex p-12">
        <div v-for="item in items" :key="item.id">
            <img src="" class="w-12" alt="">
            <p>{{ item.title }}</p>
            <p>{{ item.description }}</p>
        </div>
    </div>
</template>
