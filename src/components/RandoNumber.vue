
<script setup>
import { ref } from 'vue';

const numbers = [...Array(22).keys()].filter(num => num !== 7 && num !== 8 && num !== 22);
const randomNumber = ref(null);

const generateRandomNumber = () => {
    const randomIndex = Math.floor(Math.random() * numbers.length);
    randomNumber.value = numbers[randomIndex];
};

const resetRandomNumber = () => {
    randomNumber.value = null;
};

</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <h1>Choose</h1>
                <p>Random Number: {{ randomNumber }}</p>
                <button @click="generateRandomNumber">Generate Random Number</button>
                <button @click="resetRandomNumber">Reset</button>
            </div>
        </div>
    </div>
</template>
  
<style scoped></style>
  