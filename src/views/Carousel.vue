<template>
    <div class="carousel-home">
        <CarouselComponent 
        class="carousel" 
        v-slot="{ currentSlide }" 
        v-bind:navigation="false"
        v-bind:pagination="true"
        v-bind:startAutoPlay="true"
        v-bind:timeout="2500">
            <SlideComponent v-for="(slide, index) in carouselSlides" v-bind:key="index">
                <div v-show="currentSlide === index + 1" class="slide-info">
                    <img v-bind:src="require(`../assets/${slide}.jpg`)" alt="">
                </div>
            </SlideComponent>
        </CarouselComponent>
    </div>
</template>

<script>
import CarouselComponent from "../components/Carousel/CarouselComponent.vue"
import SlideComponent from "../components/Carousel/SlideComponent.vue"

export default {
    name: "Carousel",
    components: {
        CarouselComponent,
        SlideComponent
    },
    setup() {
        const carouselSlides = ["bg-1", "bg-2", "bg-3"]

        return { carouselSlides }
    }
}
</script>

<style scoped>
    .carousel {
        position: relative;
        max-height: 100vh;
        height: 100vh;
    }

    .slide-info {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        max-height: 100%;
        height: 100%;
    }

    img {
        min-width: 100%;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
</style>