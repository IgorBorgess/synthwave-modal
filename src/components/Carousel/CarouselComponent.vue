<template>
    <div class="carousel">
        <slot v-bind:currentSlide="currentSlide" />

        <!-- Navigation -->
        <div v-if="navEnabled" class="navigate">
            <div class="toggle-page left">
                <i @click="prevSlide" class="fa-solid fa-chevron-left"></i>
            </div>
            <div class="toggle-page right">
                <i @click="nextSlide" class="fa-solid fa-chevron-right"></i>
            </div>
        </div>

        <!-- Pagination -->
        <div v-if="paginationEnabled" class="pagination">
            <span v-for="(slide, index) in getSlideCount" 
            v-bind:key="index" 
            v-bind:class="{active : index + 1 === currentSlide}"
            @click="goToSlide(index)">
            </span>
        </div>
    </div>
</template>

<script>
import { ref, onMounted } from "vue"
export default {
    props: ["startAutoPlay", "timeout", "navigation", "pagination"],

    setup(props) {
        const currentSlide = ref(1)
        const getSlideCount = ref(null)
        const autoPlayEnabled = ref(props.startAutoPlay === undefined ? true : props.startAutoPlay)
        const timeoutDuration = ref(props.timeout === undefined ? 5000 : props.timeout)
        const paginationEnabled = ref(props.pagination === undefined ? true : props.pagination)
        const navEnabled = ref(props.navigation === undefined ? true : props.navigation)

        // Next Slider
        const nextSlide = () => {
            if (currentSlide.value === getSlideCount.value) {
                currentSlide.value = 1
                return
            }
            currentSlide.value += 1
        }

        // Previous Slider
        const prevSlide = () => {
            if (currentSlide.value === 1) {
                currentSlide.value = 1
                return
            }
            currentSlide.value -= 1
        }

        const goToSlide = (index) => {
            currentSlide.value = index + 1
        }

        // Autoplay
        const autoPlay = () => {
            setInterval(() => {
                nextSlide()
            }, timeoutDuration.value);
        }

        if (autoPlayEnabled.value) {
            autoPlay()
        }

        onMounted(() => {
            getSlideCount.value = document.querySelectorAll(".slide").length
        })

        return { currentSlide, nextSlide, prevSlide, getSlideCount, goToSlide, paginationEnabled, navEnabled }
    }
}
</script>

<style scoped>
    .navigate {
        padding: 0 16px;
        height: 100%;
        width: 100%;
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .toggle-page {
        display: flex;
        flex: 1;
    }

    .right {
        justify-content: flex-end;
    }

    i {
        cursor: pointer;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
        width: 40px;
        height: 40px;
        background-color: #6347c7;
        color: #FFF;
    }

    .pagination {
        position: absolute;
        bottom: 24px;
        width: 100%;
        display: flex;
        gap: 16px;
        justify-content: center;
        align-items: center;
    }

    span {
        cursor: pointer;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        background-color: #FFF;
        box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
    }

    .active {
        background: #6347c7;
    }
</style>