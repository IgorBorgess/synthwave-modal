<template>
    <div class="home">
      <ModalComponent @close="toggleModal" v-bind:modalActive="modalActive">
          <CarouselComponent 
            class="carousel, modal-content"
            v-slot="{ currentSlide }" 
            v-bind:timeout="2500">
              <SlideComponent v-for="(slide, index) in carouselSlides" v-bind:key="index">
                <div v-show="currentSlide === index + 1" class="slide-info">
                    <img v-bind:src="require(`../assets/${slide}.jpg`)" alt="">
                </div>
              </SlideComponent>
          </CarouselComponent>
      </ModalComponent>
      <button @click="toggleModal" type="button">Open Modal</button>
      
    </div>
    <div>
      <SocialMediaCardComponent />
    </div>
</template>

<script>
import ModalComponent from "../components/Modal/ModalComponent.vue";
import CarouselComponent from "../components/Carousel/CarouselComponent.vue"
import SlideComponent from "../components/Carousel/SlideComponent.vue"
import SocialMediaCardComponent from "../components/Card/SocialMediaCardComponent.vue"
import { ref } from 'vue';

export default {
    name: 'HomeView',
    components: {
        ModalComponent,
        CarouselComponent,
        SlideComponent,
        SocialMediaCardComponent
    },
    setup() {
        const modalActive = ref(false);

        const toggleModal = () => {
            modalActive.value = !modalActive.value;
        };

        const carouselSlides = ["bg-1", "bg-2", "bg-3"]

        return { modalActive, toggleModal, carouselSlides };
    }
};
</script>

<style scoped>
  .home {
    background-color: rgba(52,28,108,0.6);
    height: 35vh;
    display: flex;
    justify-content: center;
    align-items: flex-end;
  }

  .modal-content {
    display: flex;
    flex-direction: column;
  }

    h1, p {
      margin-bottom: 16px;
    }

    h1 {
      font-size: 36px;
    }

    p {
      font-size: 18px;
    }

    .carousel {
    position: relative;
    max-height: 75vh;
    height: 75vh;
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
