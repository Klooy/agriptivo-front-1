<template>
  <div class="video-section">
    <h1 class="text-white text-center">Maquinaria especializada</h1>

    <div class="carousel-wrapper">
      <!-- Botón Izquierda -->
      <button class="arrow left" @click="prevSlide">❮</button>

      <!-- Carrusel -->
      <div class="carousel">
        <div
          v-for="(video, index) in videos"
          :key="index"
          class="video"
          v-show="currentIndex === index"
        >
          <iframe
            :src="video.src"
            frameborder="0"
            allowfullscreen
          ></iframe>
          <p class="video-title">{{ video.title }}</p>
        </div>
      </div>

      <!-- Botón Derecha -->
      <button class="arrow right" @click="nextSlide">❯</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      videos: [
        {
          title: "Maquinaria especializada",
          src: "https://www.youtube.com/embed/YqGTHa1i2Iw",
        },
        {
          title: "Victoria - Clasificadora de frutos redondos",
          src: "https://www.youtube.com/embed/GEotmanVFy8",
        },
        {
          title: "RedBee - Monitorización de cultivos",
          src: "https://www.youtube.com/embed/5lFH8_TcKrM",
        },
      ],
    };
  },
  methods: {
    nextSlide() {
      this.currentIndex =
        (this.currentIndex + 1) % this.videos.length;
    },
    prevSlide() {
      this.currentIndex =
        (this.currentIndex - 1 + this.videos.length) %
        this.videos.length;
    },
  },
};
</script>

<style>
.video-section {
  width: 100%;
  min-height: 100vh;
  background-color: black;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem 1rem;
  position: relative;
}

.carousel-wrapper {
  position: relative;
  width: 100%;
  max-width: 900px;
}

.carousel {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.video {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.video iframe {
  width: 100%;
  height: 500px;
  border-radius: 10px;
}

.video-title {
  margin-top: 0.5rem;
  color: white;
  font-size: 1.2rem;
  text-align: center;
}

/* Flechas */
.arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255, 255, 255, 0.2);
  border: none;
  font-size: 2rem;
  color: white;
  cursor: pointer;
  padding: 0.5rem 1rem;
  border-radius: 50%;
  transition: background 0.3s;
  z-index: 10;
}

.arrow:hover {
  background: rgba(255, 255, 255, 0.5);
}

.arrow.left {
  left: -2.5rem;
}

.arrow.right {
  right: -2.5rem;
}

/* Responsive: Flechas dentro en pantallas pequeñas */
@media (max-width: 768px) {
  .arrow.left {
    left: 0.5rem;
  }
  .arrow.right {
    right: 0.5rem;
  }
}
</style>
