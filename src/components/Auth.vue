<script setup lang="ts">
import { ref } from 'vue'

const isLoginMode = ref(true)
const formData = ref({
  email: '',
  password: '',
  confirmPassword: '',
  firstName: '',
  lastName: '',
  phone: '',
  membershipType: 'basic',
  agreeToTerms: false
}) 

const isSubmitting = ref(false)
const submitMessage = ref('')
const showForgotPassword = ref(false)

const toggleMode = () => {
  isLoginMode.value = !isLoginMode.value
  resetForm()
}

const resetForm = () => {
  formData.value = {
    email: '',
    password: '',
    confirmPassword: '',
    firstName: '',
    lastName: '',
    phone: '',
    membershipType: 'basic',
    agreeToTerms: false
  }
  submitMessage.value = ''
  showForgotPassword.value = false
}

const handleSubmit = async () => {
  isSubmitting.value = true
  
  
  setTimeout(() => {
    if (isLoginMode.value) {
      submitMessage.value = 'Login succesfuldt! Velkommen tilbage.'
    } else {
      submitMessage.value = 'Konto oprettet succesfuldt! Velkommen til Tidslerne.'
    }
    isSubmitting.value = false
    
    
    setTimeout(() => {
      submitMessage.value = ''
    }, 3000)
  }, 1500)
}

const handleForgotPassword = async () => {
  if (!formData.value.email) {
    submitMessage.value = 'Indtast venligst din email adresse først.'
    return
  }
  
  isSubmitting.value = true
  
  setTimeout(() => {
    submitMessage.value = 'Instruktioner til nulstilling af adgangskode er sendt til din email.'
    isSubmitting.value = false
    showForgotPassword.value = false
    
    setTimeout(() => {
      submitMessage.value = ''
    }, 5000)
  }, 1500)
}
</script>

<template>
  <section class="auth">
    <div class="container">
      <div class="auth-header">
        <h1 class="section-title">{{ isLoginMode ? 'Log Ind' : 'Opret Konto' }}</h1>
        <p class="auth-subtitle">
          {{ isLoginMode 
            ? 'Velkommen tilbage! Log ind for at få adgang til dit medlemsområde.' 
            : 'Bliv medlem af Tidslerne og få adgang til eksklusive fordele og tjenester.' 
          }}
        </p>
      </div>
      
      <div class="auth-content">
        <div class="auth-benefits" v-if="!isLoginMode">
          <h2>Fordele ved medlemskab</h2>
          <div class="benefits-list">
            <div class="benefit-item">
              <div class="benefit-icon">
                <svg width="30" height="30" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M12 2L13.09 8.26L20 9L13.09 9.74L12 16L10.91 9.74L4 9L10.91 8.26L12 2Z" fill="#27C383"/>
                </svg>
              </div>
              <div>
                <h3>Prioriteret Support</h3>
                <p>Få hurtigere svar og prioriteret behandling</p>
              </div>
            </div>
            
            <div class="benefit-item">
              <div class="benefit-icon">
                <svg width="30" height="30" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M12 21.35L10.55 20.03C5.4 15.36 2 12.27 2 8.5C2 5.41 4.42 3 7.5 3C9.24 3 10.91 3.81 12 5.08C13.09 3.81 14.76 3 16.5 3C19.58 3 22 5.41 22 8.5C22 12.27 18.6 15.36 13.45 20.03L12 21.35Z" fill="#A7105A"/>
                </svg>
              </div>
              <div>
                <h3>Eksklusive Events</h3>
                <p>Adgang til medlemsarrangementer og workshops</p>
              </div>
            </div>
            
            <div class="benefit-item">
              <div class="benefit-icon">
                <svg width="30" height="30" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M9 12L11 14L15 10M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z" stroke="#182D4F" stroke-width="2" fill="none"/>
                </svg>
              </div>
              <div>
                <h3>Rabatter</h3>
                <p>Særlige medlemsrabatter på alle tjenester</p>
              </div>
            </div>
            
            <div class="benefit-item">
              <div class="benefit-icon">
                <svg width="30" height="30" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M12 2C6.48 2 2 6.48 2 12S6.48 22 12 22 22 17.52 22 12 17.52 2 12 2ZM13 17H11V15H13V17ZM13 13H11V7H13V13Z" fill="#27C383"/>
                </svg>
              </div>
              <div>
                <h3>Personlig Rådgivning</h3>
                <p>Direkte adgang til vores sundhedseksperter</p>
              </div>
            </div>
          </div>
        </div>
        
        <div class="auth-form-container">
          <div class="form-tabs">
            <button 
              class="tab-btn" 
              :class="{ active: isLoginMode }"
              @click="isLoginMode = true; resetForm()"
            >
              Log Ind
            </button>
            <button 
              class="tab-btn" 
              :class="{ active: !isLoginMode }"
              @click="isLoginMode = false; resetForm()"
            >
              Opret Konto
            </button>
          </div>
          
          <form @submit.prevent="handleSubmit" class="auth-form">
           
            <div v-if="!isLoginMode" class="form-row">
              <div class="form-group">
                <label for="firstName">Fornavn *</label>
                <input 
                  type="text" 
                  id="firstName" 
                  v-model="formData.firstName" 
                  required 
                  placeholder="Dit fornavn"
                />
              </div>
              
              <div class="form-group">
                <label for="lastName">Efternavn *</label>
                <input 
                  type="text" 
                  id="lastName" 
                  v-model="formData.lastName" 
                  required 
                  placeholder="Dit efternavn"
                />
              </div>
            </div>
            
            
            <div class="form-group">
              <label for="email">Email Adresse *</label>
              <input 
                type="email" 
                id="email" 
                v-model="formData.email" 
                required 
                placeholder="din@email.dk"
              />
            </div>
            
            
            <div v-if="!isLoginMode" class="form-group">
              <label for="phone">Telefonnummer</label>
              <input 
                type="tel" 
                id="phone" 
                v-model="formData.phone" 
                placeholder="+45 12 34 56 78"
              />
            </div>
            
            
            <div class="form-group">
              <label for="password">Adgangskode *</label>
              <input 
                type="password" 
                id="password" 
                v-model="formData.password" 
                required 
                :placeholder="isLoginMode ? 'Din adgangskode' : 'Minimum 8 tegn'"
                :minlength="isLoginMode ? undefined : 8"
              />
            </div>
            
            
            <div v-if="!isLoginMode" class="form-group">
              <label for="confirmPassword">Bekræft Adgangskode *</label>
              <input 
                type="password" 
                id="confirmPassword" 
                v-model="formData.confirmPassword" 
                required 
                placeholder="Gentag din adgangskode"
              />
            </div>
            
            
            <div v-if="!isLoginMode" class="form-group">
              <label for="membershipType">Medlemstype</label>
              <select id="membershipType" v-model="formData.membershipType">
                <option value="basic">Basis Medlemskab (299 kr/måned)</option>
                <option value="premium">Premium Medlemskab (599 kr/måned)</option>
                <option value="vip">VIP Medlemskab (999 kr/måned)</option>
              </select>
            </div>
            
            
            <div v-if="!isLoginMode" class="form-group checkbox-group">
              <label class="checkbox-label">
                <input 
                  type="checkbox" 
                  v-model="formData.agreeToTerms" 
                  required
                />
                <span class="checkbox-custom"></span>
                Jeg accepterer <a href="#" class="terms-link">vilkår og betingelser</a> samt <a href="#" class="terms-link">privatlivspolitik</a>
              </label>
            </div>
            
            
            <div v-if="isLoginMode" class="forgot-password">
              <button type="button" @click="showForgotPassword = true" class="forgot-link">
                Glemt adgangskode?
              </button>
            </div>
            
            
            <div class="form-actions">
              <button 
                type="submit" 
                class="btn btn-primary submit-btn"
                :disabled="isSubmitting || (!isLoginMode && !formData.agreeToTerms)"
              >
                <span v-if="isSubmitting">{{ isLoginMode ? 'Logger ind...' : 'Opretter konto...' }}</span>
                <span v-else>{{ isLoginMode ? 'Log Ind' : 'Opret Konto' }}</span>
              </button>
            </div>
            
           
            <div v-if="submitMessage" class="message" :class="{ success: !submitMessage.includes('fejl') }">
              {{ submitMessage }}
            </div>
          </form>
          
          
          <div class="social-login">
            <div class="divider">
              <span>eller</span>
            </div>
            
            <div class="social-buttons">
              <button class="social-btn google">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M22.56 12.25C22.56 11.47 22.49 10.72 22.36 10H12V14.26H17.92C17.66 15.63 16.84 16.78 15.61 17.53V20.33H19.18C21.38 18.33 22.56 15.53 22.56 12.25Z" fill="#4285F4"/>
                  <path d="M12 23C15.24 23 17.96 21.92 19.18 20.33L15.61 17.53C14.58 18.16 13.26 18.53 12 18.53C8.87 18.53 6.22 16.5 5.27 13.7H1.56V16.58C2.77 18.98 7.15 23 12 23Z" fill="#34A853"/>
                  <path d="M5.27 13.7C5.05 13.07 4.93 12.39 4.93 11.7C4.93 11.01 5.05 10.33 5.27 9.7V6.82H1.56C0.88 8.17 0.5 9.68 0.5 11.7C0.5 13.72 0.88 15.23 1.56 16.58L5.27 13.7Z" fill="#FBBC05"/>
                  <path d="M12 4.47C13.45 4.47 14.74 4.94 15.76 5.92L18.96 2.72C17.96 1.8 16.24 1.25 12 1.25C7.15 1.25 2.77 5.27 1.56 7.67L5.27 10.55C6.22 7.75 8.87 4.47 12 4.47Z" fill="#EA4335"/>
                </svg>
                {{ isLoginMode ? 'Log ind med Google' : 'Opret med Google' }}
              </button>
              
              <button class="social-btn facebook">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M24 12.073C24 5.405 18.627 0 12 0S0 5.405 0 12.073C0 18.1 4.388 23.094 10.125 24V15.564H7.078V12.073H10.125V9.405C10.125 6.348 11.917 4.688 14.658 4.688C15.97 4.688 17.344 4.922 17.344 4.922V7.875H15.83C14.34 7.875 13.875 8.8 13.875 9.75V12.073H17.203L16.671 15.564H13.875V24C19.612 23.094 24 18.1 24 12.073Z" fill="#1877F2"/>
                </svg>
                {{ isLoginMode ? 'Log ind med Facebook' : 'Opret med Facebook' }}
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    
    <div v-if="showForgotPassword" class="modal" @click="showForgotPassword = false">
      <div class="modal-content" @click.stop>
        <button class="close-btn" @click="showForgotPassword = false">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M18 6L6 18M6 6L18 18" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </button>
        
        <h2>Nulstil Adgangskode</h2>
        <p>Indtast din email adresse, så sender vi dig instruktioner til at nulstille din adgangskode.</p>
        
        <form @submit.prevent="handleForgotPassword">
          <div class="form-group">
            <label for="resetEmail">Email Adresse</label>
            <input 
              type="email" 
              id="resetEmail" 
              v-model="formData.email" 
              required 
              placeholder="din@email.dk"
            />
          </div>
          
          <div class="modal-actions">
            <button type="button" @click="showForgotPassword = false" class="btn btn-secondary">
              Annuller
            </button>
            <button type="submit" class="btn btn-primary" :disabled="isSubmitting">
              {{ isSubmitting ? 'Sender...' : 'Send Instruktioner' }}
            </button>
          </div>
        </form>
      </div>
    </div>
  </section>
</template>

<style scoped>
.auth {
  padding: 6rem 0 4rem;
  background: linear-gradient(135deg, #f8f9fa 0%, rgba(39, 195, 131, 0.05) 100%);
  min-height: 100vh;
}

.auth-header {
  text-align: center;
  margin-bottom: 4rem;
}

.auth-subtitle {
  font-size: 1.2rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}

.auth-content {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 4rem;
  align-items: start;
}

.auth-benefits {
  background: white;
  padding: 3rem;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.auth-benefits h2 {
  color: #182D4F;
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 2rem;
  text-align: center;
}

.benefits-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.benefit-item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1.5rem;
  background: linear-gradient(135deg, rgba(39, 195, 131, 0.05), rgba(167, 16, 90, 0.05));
  border-radius: 15px;
  transition: transform 0.3s ease;
}

.benefit-item:hover {
  transform: translateY(-3px);
}

.benefit-icon {
  flex-shrink: 0;
  background: white;
  padding: 0.5rem;
  border-radius: 50%;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.benefit-item h3 {
  color: #182D4F;
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 0.25rem;
}

.benefit-item p {
  color: #666;
  font-size: 0.95rem;
  margin: 0;
  line-height: 1.5;
}

.auth-form-container {
  background: white;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.form-tabs {
  display: flex;
  background: #f8f9fa;
}

.tab-btn {
  flex: 1;
  padding: 1.5rem;
  border: none;
  background: transparent;
  color: #666;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  border-bottom: 3px solid transparent;
}

.tab-btn.active {
  background: white;
  color: #182D4F;
  border-bottom-color: #27C383;
}

.auth-form {
  padding: 3rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-group label {
  color: #182D4F;
  font-weight: 600;
  margin-bottom: 0.5rem;
  font-size: 0.95rem;
}

.form-group input,
.form-group select {
  padding: 0.75rem 1rem;
  border: 2px solid #e1e5e9;
  border-radius: 10px;
  font-size: 1rem;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
  font-family: inherit;
}

.form-group input:focus,
.form-group select:focus {
  outline: none;
  border-color: #27C383;
  box-shadow: 0 0 0 3px rgba(39, 195, 131, 0.1);
}

.checkbox-group {
  margin: 1rem 0;
}

.checkbox-label {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  cursor: pointer;
  font-weight: normal;
  line-height: 1.5;
}

.checkbox-label input[type="checkbox"] {
  display: none;
}

.checkbox-custom {
  width: 20px;
  height: 20px;
  border: 2px solid #e1e5e9;
  border-radius: 4px;
  position: relative;
  transition: all 0.3s ease;
  flex-shrink: 0;
  margin-top: 2px;
}

.checkbox-label input[type="checkbox"]:checked + .checkbox-custom {
  background: #27C383;
  border-color: #27C383;
}

.checkbox-label input[type="checkbox"]:checked + .checkbox-custom::after {
  content: '✓';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 12px;
  font-weight: bold;
}

.terms-link {
  color: #A7105A;
  text-decoration: none;
  font-weight: 600;
}

.terms-link:hover {
  text-decoration: underline;
}

.forgot-password {
  text-align: right;
  margin: -0.5rem 0 0.5rem;
}

.forgot-link {
  background: none;
  border: none;
  color: #A7105A;
  font-size: 0.9rem;
  cursor: pointer;
  text-decoration: none;
}

.forgot-link:hover {
  text-decoration: underline;
}

.submit-btn {
  width: 100%;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  font-weight: 600;
  margin-top: 1rem;
}

.submit-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.message {
  padding: 1rem;
  border-radius: 10px;
  text-align: center;
  font-weight: 600;
  margin-top: 1rem;
}

.message.success {
  background: linear-gradient(135deg, #27C383, #22a36d);
  color: white;
}

.social-login {
  padding: 0 3rem 3rem;
}

.divider {
  position: relative;
  text-align: center;
  margin: 2rem 0;
}

.divider::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  height: 1px;
  background: #e1e5e9;
}

.divider span {
  background: white;
  padding: 0 1rem;
  color: #666;
  font-size: 0.9rem;
}

.social-buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.social-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  padding: 0.75rem 1rem;
  border: 2px solid #e1e5e9;
  border-radius: 10px;
  background: white;
  color: #666;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.social-btn:hover {
  border-color: #27C383;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.social-btn.google:hover {
  border-color: #4285F4;
}

.social-btn.facebook:hover {
  border-color: #1877F2;
}


.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
  padding: 2rem;
}

.modal-content {
  background: white;
  border-radius: 20px;
  padding: 3rem;
  max-width: 500px;
  width: 100%;
  position: relative;
}

.close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  color: #666;
  cursor: pointer;
  padding: 0.5rem;
  border-radius: 50%;
  transition: background 0.3s ease;
}

.close-btn:hover {
  background: #f8f9fa;
}

.modal-content h2 {
  color: #182D4F;
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.modal-content p {
  color: #666;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.modal-actions {
  display: flex;
  gap: 1rem;
  margin-top: 2rem;
}

.modal-actions .btn {
  flex: 1;
  padding: 0.75rem 1rem;
}

@media (max-width: 768px) {
  .auth-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .form-row {
    grid-template-columns: 1fr;
  }
  
  .auth-form {
    padding: 2rem;
  }
  
  .social-login {
    padding: 0 2rem 2rem;
  }
  
  .auth-benefits {
    padding: 2rem;
  }
  
  .modal-content {
    padding: 2rem;
    margin: 1rem;
  }
  
  .modal-actions {
    flex-direction: column;
  }
}
</style>