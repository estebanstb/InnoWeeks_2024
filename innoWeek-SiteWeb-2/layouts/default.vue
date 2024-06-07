<template>
    <div>
        <AppHeader class="layout" />
        <slot />
        <AppFooter class="layout" />
    </div>
</template>

<style scoped>
.layout{
    height: 10vh;
}
</style>