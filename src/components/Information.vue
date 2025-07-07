<script setup lang="ts">
</script>

<template>
  <section class="information">
    <div class="container">
      <div class="info-header">
        <h1 class="section-title">Hvem er Tidslerne?</h1>
      </div>
      
      <div class="info-content">
        <div class="main-info-card">
          <div class="info-text">
            <div class="intro-section">
              <h2>Kræftforeningen Tidslerne er patientforeningen</h2>
              <p class="highlight-text">- uafhængig af læger og medicinalindustrien.</p>
            </div>

            <div class="content-section">
              <p>
                Formålet med Tidslerne er at udbrede kendskabet til, og være bro mellem, 
                konventionel og komplementær kræftbehandling. Vi støtter vores medlemmer 
                i at vælge eller fravælge behandling. Vi mennesker er individer, og hver 
                patient må finde sin egen vej.
              </p>

              <p>
                Tidslerne arbejder for en positiv og åben dialog mellem behandler og patient, 
                samt for information om bivirkninger og evidens for behandlingsmuligheder, 
                både i det konventionelle sundhedsvæsen og inden for komplementære/alternative 
                behandlingsformer.
              </p>

              <p>
                Tidslerne giver information om konventionel og komplementær behandling 
                både i Danmark og i udlandet.
              </p>

              <p>
                Tidslerne arrangerer selvhjælpskurser og workshops for sine medlemmer 
                til en meget begrænset egenbetaling.
              </p>

              <p>
                Tidslerne blander sig i sundhedsdebatten og deltager internationalt 
                i European Cancer Patient Coalition (ECPC), www.ecpc.org.
              </p>

              <p>
                Foreningen ledes og styres af frivillige. Kun patientmedlemmer har 
                stemmeret på generalforsamlingen.
              </p>
            </div>

            <div class="values-section">
              <h3>Vores Grundværdier</h3>
              <div class="values-list">
                <div class="value-item">
                  <div class="value-icon">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                    </svg>
                  </div>
                  <span>Uafhængighed fra medicinalindustrien</span>
                </div>
                <div class="value-item">
                  <div class="value-icon">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                    </svg>
                  </div>
                  <span>Respekt for individuelle valg</span>
                </div>
                <div class="value-item">
                  <div class="value-icon">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                    </svg>
                  </div>
                  <span>Åben dialog mellem patient og behandler</span>
                </div>
                <div class="value-item">
                  <div class="value-icon">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                    </svg>
                  </div>
                  <span>Evidensbaseret information</span>
                </div>
                <div class="value-item">
                  <div class="value-icon">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#27C383" stroke-width="2" fill="none"/>
                    </svg>
                  </div>
                  <span>Internationalt samarbejde</span>
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
.information {
  padding: 6rem 0 4rem;
  background: linear-gradient(135deg, #f8f9fa 0%, rgba(39, 195, 131, 0.05) 100%);
  min-height: 100vh;
}

.info-header {
  text-align: center;
  margin-bottom: 4rem;
}

.main-info-card {
  background: white;
  border-radius: 25px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  max-width: 900px;
  margin: 0 auto;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.info-text {
  padding: 3rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.intro-section {
  margin-bottom: 2rem;
  text-align: center;
  padding-bottom: 2rem;
  border-bottom: 2px solid #f0f0f0;
}

.intro-section h2 {
  color: #182D4F;
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  line-height: 1.3;
}

.highlight-text {
  color: #A7105A;
  font-size: 1.3rem;
  font-weight: 600;
  font-style: italic;
  margin: 0;
}

.content-section {
  margin-bottom: 2rem;
}

.content-section p {
  color: #666;
  line-height: 1.8;
  margin-bottom: 1.5rem;
  font-size: 1.05rem;
  text-align: justify;
}

.values-section h3 {
  color: #182D4F;
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  text-align: center;
  position: relative;
}

.values-section h3::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 2px;
  background: #e0e0e0;
  border-radius: 2px;
}

.values-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.value-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  background: white;
  border-radius: 10px;
  border: 1px solid #f0f0f0;
  transition: all 0.3s ease;
}

.value-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
  border-color: #e0e0e0;
}

.value-icon {
  flex-shrink: 0;
}

.value-item span {
  color: #182D4F;
  font-weight: 500;
  font-size: 1rem;
}

@media (max-width: 768px) {
  .main-info-card {
    margin: 0 1rem;
  }
  
  .info-text {
    padding: 2rem;
  }
  
  .intro-section h2 {
    font-size: 1.5rem;
  }
  
  .highlight-text {
    font-size: 1.1rem;
  }
  
  .content-section p {
    font-size: 1rem;
    text-align: left;
  }
  
  .values-section h3 {
    font-size: 1.3rem;
  }
  
  .value-item {
    padding: 0.75rem;
  }
  
  .value-item span {
    font-size: 0.95rem;
  }
}

@media (max-width: 480px) {
  .info-text {
    padding: 1.5rem;
  }
  
  .intro-section h2 {
    font-size: 1.3rem;
  }
  
  .highlight-text {
    font-size: 1rem;
  }
  
  .values-list {
    gap: 0.75rem;
  }
}
</style>