<script setup lang="ts">
import { ref } from 'vue'

const selectedImage = ref<string | null>(null)
const selectedVideo = ref<string | null>(null)

const galleryImages = [
  {
    id: 1,
    src: '/mainielsen1.jpg',
    alt: 'Mai Nielsen - Formand for Tidslerne',
    category: 'Ledelse'
  },
  {
    id: 2,
    src: '/d2.png',
    alt: 'Tidslerne medlemmer samlet',
    category: 'Fællesskab'
  },
  {
    id: 3,
    src: '/article.jpg',
    alt: 'Race for Life arrangement',
    category: 'Arrangementer'
  }
]

const videoLibrary = [
  {
    id: 1,
    title: 'Tidslerne Præsentation',
    description: 'En introduktion til vores organisation og mission',
    youtubeId: 'rjm7kX3w57k',
    thumbnail: 'https://img.youtube.com/vi/rjm7kX3w57k/maxresdefault.jpg'
  },
  {
    id: 2,
    title: 'Medlemshistorier',
    description: 'Hør fra vores medlemmer om deres oplevelser',
    youtubeId: '0zR1lgEPU3I',
    thumbnail: 'https://img.youtube.com/vi/0zR1lgEPU3I/maxresdefault.jpg'
  },
  {
    id: 3,
    title: 'Sundhedstips',
    description: 'Praktiske råd til et sundere liv',
    youtubeId: 'VICqBMF06OA',
    thumbnail: 'https://img.youtube.com/vi/VICqBMF06OA/maxresdefault.jpg'
  },
  {
    id: 4,
    title: 'Fællesskab og Støtte',
    description: 'Hvordan vi støtter hinanden i Tidslerne',
    youtubeId: 'K2RdwqJU2lo',
    thumbnail: 'https://img.youtube.com/vi/K2RdwqJU2lo/maxresdefault.jpg'
  }
]

const openModal = (imageSrc: string) => {
  selectedImage.value = imageSrc
}

const closeModal = () => {
  selectedImage.value = null
}

const openVideoModal = (videoId: string) => {
  selectedVideo.value = videoId
}

const closeVideoModal = () => {
  selectedVideo.value = null
}
</script>

<template>
  <section class="gallery">
    <div class="container">
      <div class="gallery-header">
        <h1 class="section-title">Galleri</h1>
        <p class="gallery-subtitle">
          Se billeder fra vores aktiviteter, arrangementer og fællesskab
        </p>
      </div>
      
      <div class="gallery-grid">
        <div 
          v-for="image in galleryImages" 
          :key="image.id"
          class="gallery-item"
          @click="openModal(image.src)"
        >
          <div class="image-container">
            <img :src="image.src" :alt="image.alt" class="gallery-image" />
            <div class="image-overlay">
              <div class="overlay-content">
                <h3>{{ image.category }}</h3>
                <p>{{ image.alt }}</p>
                <div class="view-icon">
                  <svg width="30" height="30" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12 4.5C7 4.5 2.73 7.61 1 12C2.73 16.39 7 19.5 12 19.5S21.27 16.39 23 12C21.27 7.61 17 4.5 12 4.5ZM12 17C9.24 17 7 14.76 7 12S9.24 7 12 7S17 9.24 17 12S14.76 17 12 17ZM12 9C10.34 9 9 10.34 9 12S10.34 15 12 15S15 13.66 15 12S13.66 9 12 9Z" fill="white"/>
                  </svg>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <div class="video-library">
        <h2 class="video-title">Video Bibliotek</h2>
        <p class="video-subtitle">
          Se vores videoer og lær mere om Tidslerne, vores medlemmer og sundhedstips
        </p>
        
        <div class="video-grid">
          <div 
            v-for="video in videoLibrary" 
            :key="video.id"
            class="video-item"
            @click="openVideoModal(video.youtubeId)"
          >
            <div class="video-thumbnail-container">
              <img :src="video.thumbnail" :alt="video.title" class="video-thumbnail" />
              <div class="play-overlay">
                <div class="play-button">
                  <svg width="60" height="60" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M8 5V19L19 12L8 5Z" fill="white"/>
                  </svg>
                </div>
              </div>
            </div>
            <div class="video-content">
              <h3>{{ video.title }}</h3>
              <p>{{ video.description }}</p>
            </div>
          </div>
        </div>
      </div>
      
      <div class="gallery-info">
        <div class="info-cards">
          <div class="info-card">
            <h3>Vores Ledelse</h3>
            <p>
              Mai Nielsen leder Tidslerne som formand og arbejder dedikeret for at støtte 
              vores medlemmer og fremme foreningens mission.
            </p>
          </div>
          
          <div class="info-card">
            <h3>Stærkt Fællesskab</h3>
            <p>
              Vores medlemmer kommer sammen for at dele erfaringer, støtte hinanden 
              og skabe et varmt og inkluderende miljø.
            </p>
          </div>
          
          <div class="info-card">
            <h3>Aktive Arrangementer</h3>
            <p>
              Vi deltager i og arrangerer forskellige events som Race for Life, 
              workshops og andre aktiviteter for vores medlemmer.
            </p>
          </div>
        </div>
      </div>
    </div>
    
    
    <div v-if="selectedImage" class="modal" @click="closeModal">
      <div class="modal-content" @click.stop>
        <button class="close-btn" @click="closeModal">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M18 6L6 18M6 6L18 18" stroke="white" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </button>
        <img :src="selectedImage" alt="Gallery image" class="modal-image" />
      </div>
    </div>
    
    
    <div v-if="selectedVideo" class="modal video-modal" @click="closeVideoModal">
      <div class="modal-content video-modal-content" @click.stop>
        <button class="close-btn" @click="closeVideoModal">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M18 6L6 18M6 6L18 18" stroke="white" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </button>
        <div class="video-container">
          <iframe 
            :src="`https://www.youtube.com/embed/${selectedVideo}?autoplay=1`"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
            class="video-iframe"
          ></iframe>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.gallery {
  padding: 6rem 0 4rem;
  background: linear-gradient(135deg, #f8f9fa 0%, rgba(167, 16, 90, 0.05) 100%);
  min-height: 100vh;
}

.gallery-header {
  text-align: center;
  margin-bottom: 4rem;
}

.gallery-subtitle {
  font-size: 1.2rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 6rem;
}

.gallery-item {
  cursor: pointer;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  background: white;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.gallery-item:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
}

.image-container {
  position: relative;
  height: 300px;
  overflow: hidden;
}

.gallery-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.gallery-item:hover .gallery-image {
  transform: scale(1.1);
}

.image-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(167, 16, 90, 0.8), rgba(39, 195, 131, 0.8));
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.gallery-item:hover .image-overlay {
  opacity: 1;
}

.overlay-content {
  text-align: center;
  color: white;
  padding: 1rem;
}

.overlay-content h3 {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.overlay-content p {
  font-size: 1rem;
  margin-bottom: 1rem;
  opacity: 0.9;
}

.view-icon {
  display: flex;
  justify-content: center;
}

.video-library {
  margin-bottom: 6rem;
}

.video-title {
  font-size: 3rem;
  font-weight: 700;
  color: #182D4F;
  text-align: center;
  margin-bottom: 1rem;
  position: relative;
}

.video-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 4px;
  background: linear-gradient(90deg, #A7105A, #27C383);
  border-radius: 2px;
}

.video-subtitle {
  text-align: center;
  font-size: 1.2rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto 3rem;
  line-height: 1.6;
}

.video-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.video-item {
  background: white;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.video-item:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
}

.video-thumbnail-container {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.video-thumbnail {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.video-item:hover .video-thumbnail {
  transform: scale(1.05);
}

.play-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(24, 45, 79, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.video-item:hover .play-overlay {
  opacity: 1;
}

.play-button {
  background: linear-gradient(135deg, #A7105A, #27C383);
  border-radius: 50%;
  width: 80px;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.3s ease;
}

.play-button:hover {
  transform: scale(1.1);
}

.video-content {
  padding: 1.5rem;
}

.video-content h3 {
  color: #182D4F;
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.video-content p {
  color: #666;
  line-height: 1.6;
  margin: 0;
}

.gallery-info {
  background: white;
  padding: 3rem;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.info-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.info-card {
  text-align: center;
  padding: 2rem;
  border-radius: 15px;
  transition: transform 0.3s ease;
  background: white;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.info-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
}

.info-card h3 {
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: #182D4F;
}

.info-card p {
  line-height: 1.6;
  margin: 0;
  color: #666;
}

.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
  padding: 2rem;
}

.modal-content {
  position: relative;
  max-width: 90vw;
  max-height: 90vh;
}

.modal-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
  border-radius: 10px;
}

.video-modal-content {
  max-width: 1200px;
  width: 100%;
}

.video-container {
  position: relative;
  width: 100%;
  height: 0;
  padding-bottom: 56.25%; 
  background: #000;
  border-radius: 10px;
  overflow: hidden;
}

.video-iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.close-btn {
  position: absolute;
  top: -50px;
  right: 0;
  background: rgba(24, 45, 79, 0.8);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background 0.3s ease;
  z-index: 10;
}

.close-btn:hover {
  background: rgba(24, 45, 79, 1);
}

@media (max-width: 768px) {
  .gallery-grid {
    grid-template-columns: 1fr;
  }
  
  .video-grid {
    grid-template-columns: 1fr;
  }
  
  .info-cards {
    grid-template-columns: 1fr;
  }
  
  .gallery-info {
    padding: 2rem;
  }
  
  .modal {
    padding: 1rem;
  }
  
  .close-btn {
    top: -40px;
    right: -10px;
  }
  
  .video-title {
    font-size: 2rem;
  }
}
</style>