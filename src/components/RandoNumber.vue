<script>

import { giffArray } from "../data/giffy.js"

export default {
    data() {
        return {
            giffArray: giffArray,
            randomNumber: null,
            imageVisible: false
        };
    },
    methods: {
        generateRandomNumber() {
            let randomNum;
            do {
                randomNum = Math.floor(Math.random() * 21) + 1;
            } while (randomNum === 7 || randomNum === 8);

            this.randomNumber = randomNum;
            this.imageVisible = true; // Mostra l'immagine
        },
        resetRandomNumber() {
            this.randomNumber = null;
            this.imageVisible = false; // Nascondi l'immagine
        },
        getImagePath: function (name) {
            return new URL(`../assets/img/${name}`, import.meta.url).href
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-6">
                <h1>Choose</h1>
                <p v-if="randomNumber !== null">Random Number: {{ randomNumber }}</p>
                <p v-else>Click 'Generate Random Number' to see the number</p>
                <button @click="generateRandomNumber">Generate Random Number</button>
                <button @click="resetRandomNumber">Reset</button>
            </div>
            <div class="col-6">
                <div class="text-center p-2" v-for="giff in giffArray" :key="giff.img">
                    <img class="rounded-4" :src="getImagePath(giff.img)" alt="giff Image">
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
/* Stili CSS opzionali */
</style>
