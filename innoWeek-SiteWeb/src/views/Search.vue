<script setup>  
import {ref} from 'vue'

const step = ref(1)

const next = () => {
    if (step.value <= 2 )
    step.value+=1
}
const previous = () => {
    if(step.value >= 2)
    {
        step.value-=1
    }
}

</script>

<template>
    <div>
        <div class="step">
            <p :style="{'color': step == 1 ? 'red' : 'black'}">1</p>
            <p :style="{'color': step == 2 ? 'red' : 'black'}">2</p>
            <p :style="{'color': step == 3 ? 'red' : 'black'}">3</p>
        </div>
        <div>
            <div v-if="step == 1">
                <select name="type" id="type-devlopper" multiple>
                    <option value="frontend">frontend</option>
                    <option value="backend">backend</option>
                </select>
            </div>
            <div v-if="step == 2">
                <input type="range" min="0" max="100" />
            </div>
            <div v-if="step == 3">

            </div>
        </div>
        <div>
            <button v-if="step != 1" @click="previous">previous</button>
            <button v-if="step != 3" @click="next">next</button>
        </div>
    </div>
</template>

<style scoped>
.step{
    display: flex;
}
</style>
