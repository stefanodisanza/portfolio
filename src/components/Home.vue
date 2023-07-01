<template>
    <div class="container my-5">
        <h1 class="my-5">Benvenuti nel mondo di Stefano,
            <br>
            il mago del codice!
        </h1>
        <p>Sono un Jr. Full Stack Web Developer con un tocco di creatività e un pizzico di follia. Con la mia magia
            digitale, trasformo le tue idee in esperienze web straordinarie. Esplora il mio portfolio e lasciati incantare
            dai progetti come il mio ultimo capolavoro nel food delivery. Scopri il segreto dietro le mie creazioni digitali
            nella pagina "Chi sono". Scegli la magia del web con un tocco di umorismo e stile. Sei pronto?
        </p>
        <div class="carousel my-5">
            <div class="slides">
                <img v-if="currentImage" :src="currentImage.src" :alt="currentImage.alt">
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            currentIndex: 0,
            images: [
                { src: '/discordpiccola.png', alt: 'Immagine 1' },
                { src: '/food4youpiccola.png', alt: 'Immagine 2' },
                { src: '/phloxpiccola.png', alt: 'Immagine 3' },
                { src: '/spotifypiccola.png', alt: 'Immagine 4' }
            ]
        };
    },
    computed: {
        currentImage() {
            return this.images[this.currentIndex];
        }
    },
    mounted() {
        setInterval(() => {
            this.currentIndex = (this.currentIndex + 1) % this.images.length;
        }, 5000);
    }
};
</script>
  
<style scoped>
.carousel {
    /* Aggiunta del margine superiore per evitare sovrapposizione con la navbar */
    width: 100%;
    height: 100%;
    border-radius: 15px;
    overflow: hidden;
}

.slides {
    display: flex;
    width: 100%;
    height: 100%;
}

.slides img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
</style>
  