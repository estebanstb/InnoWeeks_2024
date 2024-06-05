<script setup lang="ts">
    const items = [
    {
        id: 1,
        name: "vue",
        image:"https://picsum.photos/600/800?random=1",
        description:"test"
    },
    {
        id: 2,
        name: "react",
        image:"https://picsum.photos/600/800?random=2",
        description:"test"
    },
    {
        id: 3,
        name: "rip",
        image:"https://picsum.photos/600/800?random=3",
        description:"test"
    }
]
</script>

<template>
    <div class="flex p-12">
        <div v-for="item in items" :key="item.id">
            <img :src="item.image" class="w-12" alt="">
            <p>{{ item.name }}</p>
            <p>{{ item.description }}</p>
        </div>
    </div>
</template>
