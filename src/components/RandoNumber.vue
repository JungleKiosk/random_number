<script>
import { giffArray } from "../data/giffy.js"

export default {
    data() {
        return {
            giffArray: giffArray,
            randomNumber: null,
            imageVisible: false,
            selectedGiff: null
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

            // Scegli una immagine a caso dal dataset giffArray
            const randomIndex = Math.floor(Math.random() * this.giffArray.length);
            this.selectedGiff = this.giffArray[randomIndex];
        },
        resetRandomNumber() {
            this.randomNumber = null;
            this.imageVisible = false; // Nascondi l'immagine
        },
        getImagePath: function (name) {
            return new URL(`../assets/img/${name}`, import.meta.url).href;
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-8">
                <h1>Choose</h1>
                <button @click="generateRandomNumber">Generate Random Number</button>
                <button @click="resetRandomNumber">Reset</button>
            </div>
            <div class="col-8">
                <p v-if="randomNumber !== null">Random Number: {{ randomNumber }}</p>
            </div>
            <div class="col-6">
                <div class="text-center p-2" v-if="imageVisible">
                    <img class="rounded-4" :src="getImagePath(selectedGiff.img)" alt="Giff Image">
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
/* Stili CSS opzionali */
</style>
