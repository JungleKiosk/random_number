<script>
import { giffArray } from "../data/giffy.js"

export default {
    data() {
        return {
            giffArray: giffArray,
            randomNumber: null,
            imageVisible: false,
            selectedGiff: null,
            /* customColors: ["#13e764", "#f2b91e", "#ef6f31", "#22ad96", "#69bf14"], */ // Aggiungi i colori desiderati qui
            randomColor: null,
            darkOverlayVisible: false // Aggiungi questa variabile
        };
    },
    methods: {
        generateRandomNumber() {
            let randomNum;
            do {
                randomNum = Math.floor(Math.random() * 21) + 1;
            } while (randomNum === 7 || randomNum === 8);

            // Scegli casualmente un colore dall'array customColors
            /* const randomColorIndex = Math.floor(Math.random() * this.customColors.length);
            this.randomColor = this.customColors[randomColorIndex]; */

            this.randomNumber = randomNum;
            this.imageVisible = true; // Mostra l'immagine
            this.darkOverlayVisible = true; // Mostra l'overlay scuro

            // Scegli una immagine a caso dal dataset giffArray
            const randomIndex = Math.floor(Math.random() * this.giffArray.length);
            this.selectedGiff = this.giffArray[randomIndex];
        },
        resetRandomNumber() {
            this.randomNumber = null;
            this.imageVisible = false; // Nascondi l'immagine
            this.darkOverlayVisible = false; // Nascondi l'overlay scuro
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
            
            <div class="row justify-content-center align-items-center ">
                <div class="col-8 col-lg-8 mx-1 text-center">
                    <button class="btn btn_rn " @click="generateRandomNumber">Generate Number</button>
                </div>
                <div class="col-4 col-lg-4 my-2 text-center">
                    <button class="btn btn-dark" @click="resetRandomNumber">Reset</button>
                </div>
            </div>

            <div class="col-8 col-lg-8 my-3">
                <h1 class="text-center" v-if="randomNumber !== null" :style="{ color: randomColor }">{{ randomNumber }}</h1>
            </div>
            <div class="col-12 col-lg-8">
                <div class="text-center p-2" v-if="imageVisible">
                    <img class="rounded-4" :src="getImagePath(selectedGiff.img)" alt="Giff Image">
                </div>
            </div>
        </div>
    </div>
</template>
  

<style>

img {
    width: 50%;
}




</style>
