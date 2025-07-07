<script setup lang="ts">
import { ref } from 'vue'

const showPrivacyPolicy = ref(false)

const emit = defineEmits<{
  setActiveSection: [section: string]
}>()

const openPrivacyPolicy = () => {
  showPrivacyPolicy.value = true
}

const closePrivacyPolicy = () => {
  showPrivacyPolicy.value = false
}

const handleKontaktClick = () => {
  emit('setActiveSection', 'contact')
}
</script>

<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-logo">
          <img src="/src/assets/Transparent Logo.png" alt="Tidslerne Logo" class="footer-logo-img" />
        </div>
        
        <div class="footer-links">
          <button @click="openPrivacyPolicy" class="privacy-link">
            Privatlivspolitik
          </button>
          <span class="separator">|</span>
          <button @click="handleKontaktClick" class="footer-link">Kontakt</button>
        </div>
        
        <div class="social-links">
          <a href="https://www.instagram.com/tidslerne/" target="_blank" rel="noopener noreferrer" class="social-link" aria-label="Instagram">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
            </svg>
          </a>
        </div>
      </div>
      
      <div class="footer-bottom">
        <p>2019 Cancer Society Journals. All rights reserved. Layout euroteam.com</p>
      </div>
    </div>
    
    
    <div v-if="showPrivacyPolicy" class="privacy-modal" @click="closePrivacyPolicy">
      <div class="modal-content" @click.stop>
        <button class="close-btn" @click="closePrivacyPolicy">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M18 6L6 18M6 6L18 18" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </button>
        
        <div class="privacy-content">
          <h1 class="privacy-title">Privatlivspolitik</h1>
          
          <div class="privacy-section">
            <h2>Kræftforeningen Tidslerne – erklæring om beskyttelse af personoplysninger</h2>
            <p>
              Det er vigtigt for Kræftforeningen Tidslerne at beskytte de personoplysninger, 
              som foreningens medlemmer stiller til rådighed.
            </p>
            <p>
              Denne fortrolighedserklæring forklarer, hvilke persondata Kræftforeningen Tidslerne 
              indsamler, og hvordan vi bruger og opbevarer disse data.
            </p>
          </div>

          <div class="privacy-section">
            <h3>Persondata som vi indsamler</h3>
            <p>
              Kræftforeningen Tidslerne indsamler data for at sikre en effektiv og sikker 
              kommunikation mellem foreningen og dens medlemmer.
            </p>
            <p>
              Kræftforeningen Tidslerne modtager oplysninger om navn, adresse, telefonnummer 
              og e-mailadresse, når et medlem tilmelder sig foreningen.
            </p>
            <p>
              Disse oplysninger opbevares på foreningens hjemmeside efter modtagelse, beskyttet 
              af en adgangskode. På dette grundlag udarbejder medlemssekretæren en intern liste 
              over disse oplysninger. Bestyrelsen for Kræftforeningen Tidslerne og særligt 
              betroede medlemmer, som har afgivet en fortrolighedserklæring, har adgang til oplysningerne.
            </p>
            <p>
              Når medlemmer i øvrigt kontakter bestyrelsen via e-mail, registreres deres navn og e-mailadresse.
            </p>
            <p>
              Kræftforeningen Tidslerne modtager IKKE og indsamler IKKE oplysninger om CPR-numre.
            </p>
            <p>
              Kræftforeningen Tidslerne indsamler ikke data fra tredjeparter.
            </p>
            <p>
              Kræftforeningen Tidslerne videregiver kun medlemmernes navne og private adresser 
              til Nets med henblik på opkrævning af medlemskontingent og betaling for deltagelse 
              i Kræftforeningen Tidslernes kurser og foredrag.
            </p>
            <p>
              Medlemmernes personlige oplysninger bruges ikke til kommercielle formål.
            </p>
            <p>
              Dataansvarlig er formanden for Kræftforeningen Tidslerne.
            </p>
          </div>

          <div class="privacy-section">
            <h3>Hvordan Kræftforeningen Tidslerne bruger persondata</h3>
            <p>
              Kræftforeningen Tidslernes bestyrelse og særligt betroede medlemmer bruger 
              de indsamlede data til følgende hovedformål:
            </p>
            <ul>
              <li>at sende beskeder, herunder meddelelser og nyhedsbreve samt forespørgsler 
                  eller generelle oplysninger til medlemmer, og</li>
              <li>at opdatere Kræftforeningen Tidslernes medlemsliste.</li>
            </ul>
          </div>

          <div class="privacy-section">
            <h3>Privatlivsrettigheder</h3>
            <p>
              Kræftforeningen Tidslerne overholder gældende lovgivning i Databeskyttelsesforordningen 
              og Databeskyttelsesloven, som træder i kraft den 25. maj 2018. Dette omfatter følgende 
              rettigheder, hvis det er relevant:
            </p>
            <ul>
              <li>Hvis behandlingen af personoplysninger er baseret på medlemmets samtykke, 
                  har medlemmet ret til at tilbagekalde dette samtykke til enhver tid med 
                  henblik på senere behandling.</li>
              <li>Medlemmet har ret til at anmode om adgang til og berigtigelse af persondata 
                  fra Kræftforeningen Tidslerne.</li>
              <li>Medlemmet har ret til at gøre indsigelse mod behandlingen af sine persondata.</li>
              <li>Medlemmet har ret til at indgive en klage til en databeskyttelsesmyndighed.</li>
            </ul>
          </div>

          <div class="privacy-section">
            <h3>Hvordan Kræftforeningen Tidslerne opbevarer og behandler persondata</h3>
            <p>
              Indsamlede persondata opbevares og behandles af nogle få særligt betroede medlemmer 
              samt bestyrelsen.
            </p>
            <p>
              Den eneste tredjepartsagent er Nets, som udsteder den årlige kontingentopkrævning.
            </p>
            <p>
              Bestyrelsen oplyser kun Nets om medlemmernes navne og private adresser.
            </p>
          </div>

          <div class="privacy-section">
            <h3>Kræftforeningen Tidslernes opbevaring af persondata</h3>
            <p>
              Medlemmernes persondata opbevares i sekretariatet og Nets så længe, det skønnes 
              nødvendigt, dvs. så længe den pågældende er medlem.
            </p>
            <p>
              Herefter slettes medlemmets persondata fra Kræftforeningen Tidslernes database.
            </p>
            <p>
              Kræftforeningen Tidslernes hjemmeside er i øjeblikket hostet af euroteam.com
            </p>
            <p>
              Bestyrelsen bruger i øjeblikket e-mail og Foreningsadministrator som platform 
              til udsendelse af nyhedsbreve mv.
            </p>
            <p>
              Medlemmernes personlige oplysninger opbevares digitalt hos Foreningsadministrator A/S.
            </p>
          </div>

          <div class="privacy-section">
            <h3>Ændringer af denne privatlivserklæring</h3>
            <p>
              Kræftforeningen Tidslerne opdaterer denne privatlivserklæring, når det er lovpligtigt, 
              eller når det i øvrigt skønnes nødvendigt.
            </p>
            <p>
              Hvis der er væsentlige ændringer i erklæringen eller i den måde, hvorpå bestyrelsen 
              bruger personoplysninger, vil sådanne ændringer blive fremlagt som forslag til 
              vedtagelse på generalforsamlingen. Væsentlige ændringer vil blive annonceret på 
              foreningens hjemmeside og foreningens Facebook-side.
            </p>
          </div>

          <div class="privacy-section">
            <h3>Hvordan man kontakter Kræftforeningen Tidslerne</h3>
            <p>
              Spørgsmål eller klager vedrørende foreningens behandling af medlemmernes personoplysninger 
              kan rettes til Kræftforeningen Tidslerne telefonisk eller via e-mail.
            </p>
            <p>
              Kontaktoplysninger kan findes på Kræftforeningen Tidslernes hjemmeside under "Bestyrelse".
            </p>
          </div>

          <div class="privacy-date">
            <p><strong>April 2020</strong></p>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #182D4F;
  color: white;
  padding: 3rem 0 1rem;
}

.footer-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 2rem;
  flex-wrap: wrap;
  gap: 2rem;
}

.footer-logo-img {
  height: 50px;
  width: auto;
}

.footer-links {
  display: flex;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}

.privacy-link,
.footer-link {
  background: none;
  border: none;
  color: white;
  text-decoration: none;
  font-size: 0.95rem;
  cursor: pointer;
  transition: color 0.3s ease;
  padding: 0.5rem;
  border-radius: 5px;
}

.privacy-link:hover,
.footer-link:hover {
  color: #27C383;
  background: rgba(39, 195, 131, 0.1);
}

.separator {
  color: rgba(255, 255, 255, 0.4);
  font-size: 0.9rem;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  color: white;
  text-decoration: none;
  transition: all 0.3s ease;
}

.social-link:hover {
  background-color: #27C383;
  transform: translateY(-2px);
}

.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding-top: 1.5rem;
  text-align: center;
}

.footer-bottom p {
  color: rgba(255, 255, 255, 0.6);
  margin: 0;
  font-size: 0.9rem;
}

/* Privacy Policy Modal */
.privacy-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 3000;
  padding: 2rem;
  overflow-y: auto;
}

.modal-content {
  background: white;
  border-radius: 20px;
  max-width: 900px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
}

.close-btn {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  background: rgba(24, 45, 79, 0.1);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 10;
  transition: all 0.3s ease;
  color: #182D4F;
}

.close-btn:hover {
  background: rgba(24, 45, 79, 0.2);
  transform: scale(1.1);
}

.privacy-content {
  padding: 3rem;
  line-height: 1.7;
}

.privacy-title {
  color: #182D4F;
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 2rem;
  text-align: center;
  border-bottom: 3px solid #27C383;
  padding-bottom: 1rem;
}

.privacy-section {
  margin-bottom: 2.5rem;
}

.privacy-section h2 {
  color: #A7105A;
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
  line-height: 1.4;
}

.privacy-section h3 {
  color: #182D4F;
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 1rem;
  border-left: 4px solid #27C383;
  padding-left: 1rem;
}

.privacy-section p {
  color: #666;
  margin-bottom: 1rem;
  text-align: justify;
}

.privacy-section ul {
  color: #666;
  margin-left: 1.5rem;
  margin-bottom: 1rem;
}

.privacy-section li {
  margin-bottom: 0.5rem;
  line-height: 1.6;
}

.privacy-date {
  text-align: center;
  padding-top: 2rem;
  border-top: 2px solid #f0f0f0;
  margin-top: 2rem;
}

.privacy-date p {
  color: #A7105A;
  font-size: 1.1rem;
  margin: 0;
}

@media (max-width: 768px) {
  .footer-content {
    flex-direction: column;
    text-align: center;
    gap: 1.5rem;
  }
  
  .footer-links {
    justify-content: center;
  }
  
  .privacy-modal {
    padding: 1rem;
  }
  
  .privacy-content {
    padding: 2rem;
  }
  
  .privacy-title {
    font-size: 2rem;
  }
  
  .privacy-section h2 {
    font-size: 1.3rem;
  }
  
  .privacy-section h3 {
    font-size: 1.1rem;
  }
  
  .close-btn {
    top: 1rem;
    right: 1rem;
  }
}

@media (max-width: 480px) {
  .footer-links {
    flex-direction: column;
    gap: 0.5rem;
  }
  
  .separator {
    display: none;
  }
  
  .privacy-content {
    padding: 1.5rem;
  }
  
  .privacy-title {
    font-size: 1.8rem;
  }
}
</style>