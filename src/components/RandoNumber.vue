<script>
export default {
    data() {
        return {
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
                <img v-if="imageVisible" src="path_to_your_image.jpg" alt="Random Image" />
            </div>
        </div>
    </div>
</template>

<style scoped>
/* Stili CSS opzionali */
</style>
