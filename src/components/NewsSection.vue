<template>
    <div class="news-section">
        <h2 class="section-title">Últimas notícias</h2>
        <div class="carousel-container">
            <div class="carousel">
                <transition-group name="slide">
                    <div v-if="currentNews" 
                         :key="currentNews.id" 
                         class="news-item"
                         :style="{ backgroundImage: `url(${currentNews.image})` }">
                        <div class="news-content">
                            <h3>{{ currentNews.title }}</h3>
                            <p>{{ currentNews.content }}</p>
                        </div>
                    </div>
                </transition-group>
            </div>

        </div>
    </div>
</template>


<script>
import { ref, computed} from 'vue'
import imagem1 from '../assets/imagem1.jpg'
import imagem2 from '../assets/imagem2.jpg'
import imagem3 from '../assets/imagem3.jpg'

export default {
    name: 'NewsSection',
    setup() {
        const newsList = ref([
            {
                id: 1,
                title: "Novo MVP",
                content: "Shai Gilgeous-Alexander é o novo MVP da temporada",
                image: imagem1
            },
            {
                id: 2,
                title: "Thunder abre 3 a 2",
                content: "O time de Oklahoma City Thunder abre 3 a 2 na série contra o Denver Nuggets",
                image: imagem2
            },
            {
                id: 3,
                title: "Nikola Jokic fica em Denver?",
                content: "Rumores crescem sobre a possível saída de Nikola Jokic do Denver Nuggets",
                image: imagem3
            }
        ])

        const currentIndex = ref(0)
        
        const currentNews = computed(() => newsList.value[currentIndex.value])

        const nextNews = () => {
            currentIndex.value = (currentIndex.value + 1) % newsList.value.length
        }

        const previousNews = () => {
            currentIndex.value = currentIndex.value === 0 
                ? newsList.value.length - 1 
                : currentIndex.value - 1
        }

        // Auto-advance every 5 seconds
        setInterval(nextNews, 5000)

        return {
            currentNews,
            nextNews,
            previousNews
        }
    }
}
</script>

<style scoped>
.news-section {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

.section-title {
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2rem;
    color: #333;
}

.carousel-container {
    width: 100%;
    height: 500px;
    position: relative;
    margin: 0 auto;
    overflow: hidden;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.carousel {
    width: 100%;
    height: 100%;
    position: relative;
}

.news-item {
    position: absolute;
    width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    display: flex;
    align-items: flex-end;
}

.news-content {
    width: 100%;
    padding: 2rem;
    background: linear-gradient(transparent, rgba(0, 0, 0, 0.8));
    color: white;
}

h3 {
    font-size: 1.8rem;
    margin-bottom: 1rem;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

p {
    font-size: 1.2rem;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
    margin-bottom: 1rem;
}

.carousel-controls {
    position: absolute;
    bottom: 2rem;
    width: 100%;
    display: flex;
    justify-content: space-between;
    padding: 0 2rem;
    z-index: 10;
}

button {
    padding: 0.8rem 1.5rem;
    font-size: 1rem;
    background: rgba(0, 0, 0, 0.6);
    color: white;
    border: 2px solid white;
    border-radius: 4px;
    cursor: pointer;
    transition: all 0.3s ease;
}

button:hover {
    background: rgba(0, 0, 0, 0.8);
    transform: scale(1.05);
}

.slide-enter-active,
.slide-leave-active {
    transition: all 0.5s ease;
}

.slide-enter-from {
    transform: translateX(100%);
}

.slide-leave-to {
    transform: translateX(-100%);
}
</style>