<script setup lang="ts">
import { ref } from 'vue'

const emit = defineEmits<{
  setActiveSection: [section: string]
}>()

const selectedProduct = ref<string | null>(null)
const newsletterEmail = ref('')
const newsletterSubmitting = ref(false)
const newsletterMessage = ref('')

const openProductModal = (productId: string) => {
  selectedProduct.value = productId
}

const closeProductModal = () => {
  selectedProduct.value = null
}

const handleKontaktClick = () => {
  emit('setActiveSection', 'contact')
}

const handleLaesMereClick = () => {
  emit('setActiveSection', 'information')
}

const handleNewsletterSubmit = async () => {
  if (!newsletterEmail.value) {
    newsletterMessage.value = 'Indtast venligst din email adresse.'
    return
  }
  
  newsletterSubmitting.value = true
  
  
  setTimeout(() => {
    newsletterMessage.value = 'Tak! Du er nu tilmeldt vores nyhedsbrev.'
    newsletterSubmitting.value = false
    newsletterEmail.value = ''
    
    
    setTimeout(() => {
      newsletterMessage.value = ''
    }, 5000)
  }, 1500)
}

const products = [
  {
    id: 'black-tshirt',
    name: 'Tidslerne T-shirt - Sort',
    description: 'Klassisk sort t-shirt med Tidslerne logo på ryggen',
    price: '199 kr',
    frontImage: '/1.jpg',
    backImage: '/2.jpg',
    color: 'Sort'
  },
  {
    id: 'white-tshirt',
    name: 'Tidslerne T-shirt - Hvid',
    description: 'Elegant hvid t-shirt med Tidslerne logo på ryggen',
    price: '199 kr',
    frontImage: '/3.jpg',
    backImage: '/4.jpg',
    color: 'Hvid'
  }
]
</script>

<template>
  <section class="home">
    <div class="hero">
      <div class="hero-image-container">
        <img src="/img8.jpg" alt="Tidslerne Team" class="hero-background" />
        <div class="hero-overlay"></div>
      </div>
      <div class="container">
        <div class="hero-content">
          <div class="hero-text">
            <h1 class="hero-title">
              Velkommen til <span class="highlight">Tidslerne</span>
            </h1>
            <p class="hero-description">
              Vi tilbyder professionel sundhedspleje og omsorg med fokus på kvalitet, 
              empati og individuelle behov. Vores erfarne team er her for at hjælpe dig.
            </p>
            <div class="hero-buttons">
              <button class="btn btn-primary" @click="handleKontaktClick">Kontakt Os</button>
              <button class="btn btn-secondary" @click="handleLaesMereClick">Læs Mere</button>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <div class="features">
      <div class="container">
        <h2 class="section-title">Vores Tjenester</h2>
        <div class="features-grid">
          <div class="feature-card">
            <div class="feature-icon">
              <svg width="60" height="60" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 2L13.09 8.26L20 9L13.09 9.74L12 16L10.91 9.74L4 9L10.91 8.26L12 2Z" fill="#A7105A"/>
              </svg>
            </div>
            <h3>Professionel Pleje</h3>
            <p>Højkvalificeret personale med mange års erfaring inden for sundhedspleje og omsorg.</p>
          </div>
          
          <div class="feature-card">
            <div class="feature-icon">
              <svg width="60" height="60" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 21.35L10.55 20.03C5.4 15.36 2 12.27 2 8.5C2 5.41 4.42 3 7.5 3C9.24 3 10.91 3.81 12 5.08C13.09 3.81 14.76 3 16.5 3C19.58 3 22 5.41 22 8.5C22 12.27 18.6 15.36 13.45 20.03L12 21.35Z" fill="#27C383"/>
              </svg>
            </div>
            <h3>Individuel Omsorg</h3>
            <p>Vi tilpasser vores tjenester til hver enkelt patients specifikke behov og ønsker.</p>
          </div>
          
          <div class="feature-card">
            <div class="feature-icon">
              <svg width="60" height="60" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 2C6.48 2 2 6.48 2 12S6.48 22 12 22 22 17.52 22 12 17.52 2 12 2ZM13 17H11V15H13V17ZM13 13H11V7H13V13Z" fill="#182D4F"/>
              </svg>
            </div>
            <h3>24/7 Support</h3>
            <p>Vi er altid tilgængelige når du har brug for os, døgnet rundt alle ugens dage.</p>
          </div>
        </div>
      </div>
    </div>

    <div class="newsletter">
      <div class="container">
        <div class="newsletter-content">
          <div class="newsletter-text">
            <h2 class="newsletter-title">Hold dig opdateret</h2>
            <p class="newsletter-description">
              Tilmeld dig vores nyhedsbrev og få de seneste nyheder, sundhedstips og information 
              om kommende arrangementer direkte i din indbakke.
            </p>
            <div class="newsletter-benefits">
              <div class="benefit">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                </svg>
                <span>Månedlige sundhedstips</span>
              </div>
              <div class="benefit">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                </svg>
                <span>Information om arrangementer</span>
              </div>
              <div class="benefit">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                </svg>
                <span>Eksklusive medlemsfordele</span>
              </div>
            </div>
          </div>
          
          <div class="newsletter-form-container">
            <form @submit.prevent="handleNewsletterSubmit" class="newsletter-form">
              <div class="form-header">
                <div class="newsletter-icon">
                  <svg width="40" height="40" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M20 4H4C2.9 4 2.01 4.9 2.01 6L2 18C2 19.1 2.9 20 4 20H20C21.1 20 22 19.1 22 18V6C22 4.9 21.1 4 20 4ZM20 8L12 13L4 8V6L12 11L20 6V8Z" fill="#A7105A"/>
                  </svg>
                </div>
                <h3>Tilmeld Nyhedsbrev</h3>
              </div>
              
              <div class="form-group">
                <label for="newsletterEmail">Email Adresse</label>
                <input 
                  type="email" 
                  id="newsletterEmail" 
                  v-model="newsletterEmail" 
                  required 
                  placeholder="din@email.dk"
                  :disabled="newsletterSubmitting"
                />
              </div>
              
              <button 
                type="submit" 
                class="btn btn-primary newsletter-btn"
                :disabled="newsletterSubmitting"
              >
                <span v-if="newsletterSubmitting">Tilmelder...</span>
                <span v-else">Tilmeld Nyhedsbrev</span>
              </button>
              
              <div v-if="newsletterMessage" class="newsletter-message" :class="{ success: !newsletterMessage.includes('fejl') }">
                {{ newsletterMessage }}
              </div>
              
              <p class="privacy-note">
                Vi respekterer dit privatliv. Du kan afmelde dig når som helst.
              </p>
            </form>
          </div>
        </div>
      </div>
    </div>

    <div class="merchandise">
      <div class="container">
        <h2 class="section-title">Støt Tidslerne</h2>
        <p class="merch-subtitle">
          Køb vores officielle merchandise og vis din støtte til Tidslerne. Alle indtægter går til at forbedre vores tjenester.
        </p>
        <div class="merch-grid">
          <div 
            v-for="product in products" 
            :key="product.id"
            class="merch-item"
            @click="openProductModal(product.id)"
          >
            <div class="merch-image-container">
              <div class="product-showcase">
                <div class="product-side front">
                  <img :src="product.frontImage" :alt="`${product.name} - Front`" class="product-img" />
                  <div class="side-label">Front</div>
                </div>
                <div class="product-side back">
                  <img :src="product.backImage" :alt="`${product.name} - Back`" class="product-img" />
                  <div class="side-label">Ryg</div>
                </div>
              </div>
              <div class="view-overlay">
                <div class="view-icon">
                  <svg width="30" height="30" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12 4.5C7 4.5 2.73 7.61 1 12C2.73 16.39 7 19.5 12 19.5S21.27 16.39 23 12C21.27 7.61 17 4.5 12 4.5ZM12 17C9.24 17 7 14.76 7 12S9.24 7 12 7S17 9.24 17 12S14.76 17 12 17ZM12 9C10.34 9 9 10.34 9 12S10.34 15 12 15S15 13.66 15 12S13.66 9 12 9Z" fill="white"/>
                  </svg>
                </div>
                <p>Klik for at se detaljer</p>
              </div>
            </div>
            <div class="merch-content">
              <h3>{{ product.name }}</h3>
              <p class="merch-description">{{ product.description }}</p>
              <div class="merch-details">
                <span class="price">{{ product.price }}</span>
                <div class="sizes">
                  <span>Størrelser: S, M, L, XL</span>
                </div>
              </div>
              <button class="btn btn-primary merch-btn" @click.stop="openProductModal(product.id)">
                Se Detaljer & Køb
              </button>
            </div>
          </div>
        </div>
        
        <div class="merch-info">
          <div class="info-box">
            <div class="info-icon">
              <svg width="40" height="40" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 2L15.09 8.26L22 9L15.09 9.74L12 16L8.91 9.74L2 9L8.91 8.26L12 2Z" fill="#A7105A"/>
              </svg>
            </div>
            <h4>Gratis Fragt</h4>
            <p>Ved køb over 300 kr</p>
          </div>
          <div class="info-box">
            <div class="info-icon">
              <svg width="40" height="40" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M13 3C13.55 3 14 3.45 14 4V12L15.5 10.5C15.89 10.11 16.56 10.11 16.95 10.5C17.34 10.89 17.34 11.56 16.95 11.95L13.95 14.95C13.56 15.34 12.89 15.34 12.5 14.95L9.5 11.95C9.11 11.56 9.11 10.89 9.5 10.5C9.89 10.11 10.56 10.11 10.95 10.5L12 11.5V4C12 3.45 12.45 3 13 3ZM6 19C6 20.1 6.9 21 8 21H18C19.1 21 20 20.1 20 19V14H18V19H8V14H6V19Z" fill="#27C383"/>
              </svg>
            </div>
            <h4>Hurtig Levering</h4>
            <p>2-3 hverdage</p>
          </div>
          <div class="info-box">
            <div class="info-icon">
              <svg width="40" height="40" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 21.35L10.55 20.03C5.4 15.36 2 12.27 2 8.5C2 5.41 4.42 3 7.5 3C9.24 3 10.91 3.81 12 5.08C13.09 3.81 14.76 3 16.5 3C19.58 3 22 5.41 22 8.5C22 12.27 18.6 15.36 13.45 20.03L12 21.35Z" fill="#182D4F"/>
              </svg>
            </div>
            <h4>Støt En God Sag</h4>
            <p>100% af overskuddet går til Tidslerne</p>
          </div>
        </div>
      </div>
    </div>

    <div class="events">
      <div class="container">
        <h2 class="section-title">Kommende Begivenheder</h2>
        <div class="events-grid">
          <div class="event-card">
            <div class="event-date">
              <span class="day">15</span>
              <span class="month">FEB</span>
            </div>
            <div class="event-content">
              <h3>Sundhedsworkshop</h3>
              <p class="event-time">10:00 - 14:00</p>
              <p class="event-description">
                Lær om forebyggende sundhed og wellness strategier for hverdagen.
              </p>
              <div class="event-location">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22S19 14.25 19 9C19 5.13 15.87 2 12 2ZM12 11.5C10.62 11.5 9.5 10.38 9.5 9S10.62 6.5 12 6.5S14.5 7.62 14.5 9S13.38 11.5 12 11.5Z" fill="#A7105A"/>
                </svg>
                <span>Tidslerne Klinik</span>
              </div>
            </div>
          </div>

          <div class="event-card">
            <div class="event-date">
              <span class="day">22</span>
              <span class="month">FEB</span>
            </div>
            <div class="event-content">
              <h3>Gratis Sundhedstjek</h3>
              <p class="event-time">09:00 - 16:00</p>
              <p class="event-description">
                Få et gratis grundlæggende sundhedstjek med vores specialister.
              </p>
              <div class="event-location">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22S19 14.25 19 9C19 5.13 15.87 2 12 2ZM12 11.5C10.62 11.5 9.5 10.38 9.5 9S10.62 6.5 12 6.5S14.5 7.62 14.5 9S13.38 11.5 12 11.5Z" fill="#A7105A"/>
                </svg>
                <span>Tidslerne Klinik</span>
              </div>
            </div>
          </div>

          <div class="event-card">
            <div class="event-date">
              <span class="day">05</span>
              <span class="month">MAR</span>
            </div>
            <div class="event-content">
              <h3>Medlemsmøde</h3>
              <p class="event-time">18:00 - 20:00</p>
              <p class="event-description">
                Månedligt møde for medlemmer med information og netværk.
              </p>
              <div class="event-location">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22S19 14.25 19 9C19 5.13 15.87 2 12 2ZM12 11.5C10.62 11.5 9.5 10.38 9.5 9S10.62 6.5 12 6.5S14.5 7.62 14.5 9S13.38 11.5 12 11.5Z" fill="#A7105A"/>
                </svg>
                <span>Konferencelokale</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    
    <div v-if="selectedProduct" class="product-modal" @click="closeProductModal">
      <div class="modal-content" @click.stop>
        <button class="close-btn" @click="closeProductModal">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M18 6L6 18M6 6L18 18" stroke="white" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </button>
        
        <div v-for="product in products" :key="product.id">
          <div v-if="product.id === selectedProduct" class="product-details">
            <div class="product-images">
              <div class="image-viewer">
                <div class="main-image">
                  <img :src="product.frontImage" :alt="`${product.name} - Front`" class="modal-product-img" />
                </div>
                <div class="image-thumbnails">
                  <img :src="product.frontImage" :alt="Front" class="thumbnail active" />
                  <img :src="product.backImage" :alt="Back" class="thumbnail" />
                </div>
              </div>
            </div>
            
            <div class="product-info">
              <h2>{{ product.name }}</h2>
              <p class="product-description">{{ product.description }}</p>
              
              <div class="product-price">
                <span class="price-amount">{{ product.price }}</span>
              </div>
              
              <div class="product-options">
                <div class="size-selector">
                  <label>Størrelse:</label>
                  <div class="size-buttons">
                    <button class="size-btn">S</button>
                    <button class="size-btn active">M</button>
                    <button class="size-btn">L</button>
                    <button class="size-btn">XL</button>
                  </div>
                </div>
                
                <div class="quantity-selector">
                  <label>Antal:</label>
                  <div class="quantity-controls">
                    <button class="qty-btn">-</button>
                    <span class="quantity">1</span>
                    <button class="qty-btn">+</button>
                  </div>
                </div>
              </div>
              
              <div class="modal-actions">
                <button class="btn btn-primary add-to-cart">Tilføj til kurv</button>
                <button class="btn btn-secondary buy-now">Køb nu</button>
              </div>
              
              <div class="product-features">
                <div class="feature">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                  </svg>
                  <span>100% bomuld</span>
                </div>
                <div class="feature">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                  </svg>
                  <span>Miljøvenligt print</span>
                </div>
                <div class="feature">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                  </svg>
                  <span>Maskinvaskbar</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.home {
  padding-top: 80px;
}

.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
}

.hero-image-container {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1;
}

.hero-background {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  filter: brightness(1.1) contrast(1.05);
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg, 
    rgba(255, 255, 255, 0.15) 0%, 
    rgba(24, 45, 79, 0.3) 30%, 
    rgba(167, 16, 90, 0.4) 70%, 
    rgba(39, 195, 131, 0.3) 100%
  );
  backdrop-filter: blur(1px);
}

.hero-content {
  position: relative;
  z-index: 2;
  text-align: center;
  color: white;
  max-width: 800px;
  margin: 0 auto;
}

.hero-title {
  font-size: 4rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  line-height: 1.2;
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.5);
  color: white;
}

.highlight {
  color: #27C383;
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.7);
}

.hero-description {
  font-size: 1.3rem;
  margin-bottom: 2.5rem;
  line-height: 1.8;
  text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.5);
  opacity: 0.95;
  color: white;
  background: rgba(0, 0, 0, 0.2);
  padding: 1.5rem;
  border-radius: 15px;
  backdrop-filter: blur(5px);
}

.hero-buttons {
  display: flex;
  gap: 1.5rem;
  justify-content: center;
  flex-wrap: wrap;
}

.features {
  padding: 6rem 0;
  background: white;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.feature-card {
  padding: 3rem 2rem;
  border-radius: 20px;
  text-align: center;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  background: white;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.feature-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
}

.feature-icon {
  margin-bottom: 1.5rem;
  display: flex;
  justify-content: center;
}

.feature-card h3 {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: #182D4F;
}

.feature-card p {
  line-height: 1.6;
  color: #666;
}

.newsletter {
  padding: 6rem 0;
  background: linear-gradient(135deg, #182D4F 0%, #1e3558 100%);
  color: white;
}

.newsletter-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.newsletter-title {
  font-size: 3rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  color: white;
}

.newsletter-description {
  font-size: 1.2rem;
  line-height: 1.7;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.newsletter-benefits {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.benefit {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 1rem;
  opacity: 0.95;
}

.newsletter-form-container {
  background: white;
  border-radius: 20px;
  padding: 3rem;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
}

.form-header {
  text-align: center;
  margin-bottom: 2rem;
}

.newsletter-icon {
  margin-bottom: 1rem;
  display: flex;
  justify-content: center;
}

.form-header h3 {
  color: #182D4F;
  font-size: 1.5rem;
  font-weight: 600;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  color: #182D4F;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.form-group input {
  width: 100%;
  padding: 0.75rem 1rem;
  border: 2px solid #e1e5e9;
  border-radius: 10px;
  font-size: 1rem;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
  font-family: inherit;
}

.form-group input:focus {
  outline: none;
  border-color: #27C383;
  box-shadow: 0 0 0 3px rgba(39, 195, 131, 0.1);
}

.form-group input:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.newsletter-btn {
  width: 100%;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.newsletter-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.newsletter-message {
  padding: 1rem;
  border-radius: 10px;
  text-align: center;
  font-weight: 600;
  margin-bottom: 1rem;
  background: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}

.newsletter-message.success {
  background: #d4edda;
  color: #155724;
  border-color: #c3e6cb;
}

.privacy-note {
  font-size: 0.9rem;
  color: #666;
  text-align: center;
  margin: 0;
  line-height: 1.5;
}

.merchandise {
  padding: 6rem 0;
  background: linear-gradient(135deg, #f8f9fa 0%, rgba(39, 195, 131, 0.05) 100%);
}

.merch-subtitle {
  text-align: center;
  font-size: 1.2rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto 3rem;
  line-height: 1.6;
}

.merch-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 3rem;
  margin-bottom: 3rem;
}

.merch-item {
  background: white;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.merch-item:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
}

.merch-image-container {
  position: relative;
  height: 350px;
  overflow: hidden;
  background: #f8f9fa;
}

.product-showcase {
  position: relative;
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
  transition: transform 0.6s ease;
}

.merch-item:hover .product-showcase {
  transform: rotateY(180deg);
}

.product-side {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.product-side.back {
  transform: rotateY(180deg);
}

.product-img {
  width: 80%;
  height: 80%;
  object-fit: contain;
  transition: transform 0.3s ease;
}

.side-label {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(24, 45, 79, 0.9);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 600;
}

.view-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(167, 16, 90, 0.9), rgba(39, 195, 131, 0.9));
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
  color: white;
  text-align: center;
}

.merch-item:hover .view-overlay {
  opacity: 1;
}

.view-icon {
  margin-bottom: 1rem;
}

.merch-content {
  padding: 2rem;
}

.merch-content h3 {
  font-size: 1.5rem;
  font-weight: 600;
  color: #182D4F;
  margin-bottom: 0.5rem;
}

.merch-description {
  color: #666;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.merch-details {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
  gap: 1rem;
}

.price {
  font-size: 1.5rem;
  font-weight: 700;
  color: #A7105A;
}

.sizes {
  font-size: 0.9rem;
  color: #666;
}

.merch-btn {
  width: 100%;
  padding: 1rem;
  font-size: 1.1rem;
}

.merch-info {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-top: 3rem;
}

.info-box {
  text-align: center;
  padding: 2.5rem 2rem;
  border-radius: 15px;
  transition: transform 0.3s ease;
  background: white;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.info-box:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.12);
}

.info-icon {
  margin-bottom: 1rem;
  display: flex;
  justify-content: center;
}

.info-box h4 {
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: #182D4F;
}

.info-box p {
  margin: 0;
  color: #666;
}

.events {
  padding: 6rem 0;
  background: white;
}

.events-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.event-card {
  background: white;
  border-radius: 15px;
  padding: 2rem;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  gap: 1.5rem;
  border: 1px solid rgba(0, 0, 0, 0.05);
  border-left: 4px solid #27C383;
}

.event-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.12);
}

.event-date {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #A7105A, #27C383);
  color: white;
  border-radius: 10px;
  padding: 1rem;
  min-width: 80px;
  text-align: center;
}

.event-date .day {
  font-size: 2rem;
  font-weight: 700;
  line-height: 1;
}

.event-date .month {
  font-size: 0.9rem;
  font-weight: 600;
  text-transform: uppercase;
}

.event-content {
  flex: 1;
}

.event-content h3 {
  color: #182D4F;
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.event-time {
  color: #A7105A;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.event-description {
  color: #666;
  line-height: 1.6;
  margin-bottom: 1rem;
}

.event-location {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #666;
  font-size: 0.9rem;
}


.product-modal {
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
  background: white;
  border-radius: 20px;
  max-width: 1000px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
}

.close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(24, 45, 79, 0.8);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 10;
  transition: background 0.3s ease;
}

.close-btn:hover {
  background: rgba(24, 45, 79, 1);
}

.product-details {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  padding: 3rem;
}

.product-images {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.main-image {
  background: #f8f9fa;
  border-radius: 15px;
  padding: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-product-img {
  width: 100%;
  max-width: 300px;
  height: auto;
  object-fit: contain;
}

.image-thumbnails {
  display: flex;
  gap: 1rem;
  justify-content: center;
}

.thumbnail {
  width: 80px;
  height: 80px;
  object-fit: cover;
  border-radius: 10px;
  cursor: pointer;
  border: 2px solid transparent;
  transition: border-color 0.3s ease;
}

.thumbnail.active,
.thumbnail:hover {
  border-color: #27C383;
}

.product-info h2 {
  color: #182D4F;
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.product-description {
  color: #666;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.product-price {
  margin-bottom: 2rem;
}

.price-amount {
  font-size: 2.5rem;
  font-weight: 700;
  color: #A7105A;
}

.product-options {
  margin-bottom: 2rem;
}

.size-selector,
.quantity-selector {
  margin-bottom: 1.5rem;
}

.size-selector label,
.quantity-selector label {
  display: block;
  color: #182D4F;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.size-buttons {
  display: flex;
  gap: 0.5rem;
}

.size-btn {
  padding: 0.75rem 1rem;
  border: 2px solid #e1e5e9;
  background: white;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: 600;
}

.size-btn:hover,
.size-btn.active {
  border-color: #27C383;
  background: #27C383;
  color: white;
}

.quantity-controls {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.qty-btn {
  width: 40px;
  height: 40px;
  border: 2px solid #e1e5e9;
  background: white;
  border-radius: 8px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 600;
  transition: all 0.3s ease;
}

.qty-btn:hover {
  border-color: #27C383;
  background: #27C383;
  color: white;
}

.quantity {
  font-size: 1.2rem;
  font-weight: 600;
  color: #182D4F;
  min-width: 30px;
  text-align: center;
}

.modal-actions {
  display: flex;
  gap: 1rem;
  margin-bottom: 2rem;
}

.add-to-cart,
.buy-now {
  flex: 1;
  padding: 1rem;
  font-size: 1.1rem;
  font-weight: 600;
}

.product-features {
  border-top: 1px solid #e1e5e9;
  padding-top: 1.5rem;
}

.feature {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 0.5rem;
  color: #666;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-description {
    font-size: 1.1rem;
  }
  
  .hero-buttons {
    flex-direction: column;
    align-items: center;
  }
  
  .features-grid,
  .events-grid {
    grid-template-columns: 1fr;
  }
  
  .newsletter-content {
    grid-template-columns: 1fr;
    gap: 3rem;
    text-align: center;
  }
  
  .newsletter-title {
    font-size: 2rem;
  }
  
  .newsletter-form-container {
    padding: 2rem;
  }
  
  .merch-grid {
    grid-template-columns: 1fr;
  }
  
  .merch-details {
    flex-direction: column;
    align-items: flex-start;
  }
  
  .event-card {
    flex-direction: column;
    text-align: center;
  }
  
  .event-date {
    align-self: center;
  }
  
  .product-details {
    grid-template-columns: 1fr;
    gap: 2rem;
    padding: 2rem;
  }
  
  .modal-actions {
    flex-direction: column;
  }
}
</style>