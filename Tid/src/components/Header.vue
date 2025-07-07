<script setup lang="ts">
import { ref } from 'vue'

defineProps<{
  activeSection: string
}>()

const emit = defineEmits<{
  setActiveSection: [section: string]
}>()

const mobileMenuOpen = ref(false)
const userMenuOpen = ref(false)
const isLoggedIn = ref(false) 

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const toggleUserMenu = () => {
  userMenuOpen.value = !userMenuOpen.value
}

const handleNavClick = (section: string) => {
  emit('setActiveSection', section)
  mobileMenuOpen.value = false
}

const handleLogout = () => {
  isLoggedIn.value = false
  userMenuOpen.value = false
  
}
</script>

<template>
  <header class="header">
    <div class="container">
      <nav class="nav">
        <div class="logo">
          <img src="/src/assets/Transparent Logo.png" alt="Tidslerne Logo" class="logo-img" />
        </div>
        
        <ul class="nav-links" :class="{ 'nav-links-open': mobileMenuOpen }">
          <li>
            <a 
              href="#" 
              @click.prevent="handleNavClick('home')"
              :class="{ active: activeSection === 'home' }"
            >
              Hjem
            </a>
          </li>
          <li>
            <a 
              href="#" 
              @click.prevent="handleNavClick('information')"
              :class="{ active: activeSection === 'information' }"
            >
              Information
            </a>
          </li>
          <li>
            <a 
              href="#" 
              @click.prevent="handleNavClick('gallery')"
              :class="{ active: activeSection === 'gallery' }"
            >
              Galleri
            </a>
          </li>
          <li>
            <a 
              href="#" 
              @click.prevent="handleNavClick('contact')"
              :class="{ active: activeSection === 'contact' }"
            >
              Kontakt
            </a>
          </li>
        </ul>
        
        <div class="nav-actions">
          <div v-if="!isLoggedIn" class="auth-buttons">
            <button 
              @click="handleNavClick('auth')" 
              class="btn-auth login"
              :class="{ active: activeSection === 'auth' }"
            >
              Log Ind
            </button>
          </div>
          
          <div v-else class="user-menu" @click="toggleUserMenu">
            <div class="user-avatar">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 12C14.7614 12 17 9.76142 17 7C17 4.23858 14.7614 2 12 2C9.23858 2 7 4.23858 7 7C7 9.76142 9.23858 12 12 12Z" fill="currentColor"/>
                <path d="M12 14C7.58172 14 4 17.5817 4 22H20C20 17.5817 16.4183 14 12 14Z" fill="currentColor"/>
              </svg>
            </div>
            <div class="user-dropdown" :class="{ open: userMenuOpen }">
              <a href="#" class="dropdown-item">Min Profil</a>
              <a href="#" class="dropdown-item">Medlemsområde</a>
              <a href="#" class="dropdown-item">Indstillinger</a>
              <div class="dropdown-divider"></div>
              <button @click="handleLogout" class="dropdown-item logout">Log Ud</button>
            </div>
          </div>
        </div>
        
        <button class="mobile-menu-btn" @click="toggleMobileMenu">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.header {
  background-color: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 0;
}

.logo-img {
  height: 50px;
  width: auto;
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
}

.nav-links a {
  text-decoration: none;
  color: #182D4F;
  font-weight: 500;
  font-size: 1.1rem;
  padding: 0.5rem 1rem;
  border-radius: 25px;
  transition: all 0.3s ease;
  position: relative;
}

.nav-links a:hover {
  color: #A7105A;
  background-color: rgba(167, 16, 90, 0.1);
}

.nav-links a.active {
  color: #A7105A;
  background-color: rgba(167, 16, 90, 0.15);
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.auth-buttons {
  display: flex;
  gap: 0.5rem;
}

.btn-auth {
  padding: 0.5rem 1.5rem;
  border-radius: 25px;
  font-weight: 600;
  font-size: 0.95rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
  border: none;
}

.btn-auth.login {
  background: white;
  color: #182D4F;
  border: 1px solid #e0e0e0;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.btn-auth.login:hover,
.btn-auth.login.active {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
  border-color: #d0d0d0;
}

.user-menu {
  position: relative;
  cursor: pointer;
}

.user-avatar {
  width: 40px;
  height: 40px;
  background: linear-gradient(135deg, #A7105A, #27C383);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  transition: transform 0.3s ease;
}

.user-avatar:hover {
  transform: scale(1.1);
}

.user-dropdown {
  position: absolute;
  top: 100%;
  right: 0;
  background: white;
  border-radius: 10px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  min-width: 200px;
  opacity: 0;
  visibility: hidden;
  transform: translateY(-10px);
  transition: all 0.3s ease;
  margin-top: 0.5rem;
}

.user-dropdown.open {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
}

.dropdown-item {
  display: block;
  padding: 0.75rem 1rem;
  color: #182D4F;
  text-decoration: none;
  transition: background 0.3s ease;
  border: none;
  background: none;
  width: 100%;
  text-align: left;
  cursor: pointer;
}

.dropdown-item:hover {
  background: #f8f9fa;
}

.dropdown-item.logout {
  color: #A7105A;
}

.dropdown-divider {
  height: 1px;
  background: #e1e5e9;
  margin: 0.5rem 0;
}

.mobile-menu-btn {
  display: none;
  flex-direction: column;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
}

.mobile-menu-btn span {
  width: 25px;
  height: 3px;
  background-color: #182D4F;
  margin: 3px 0;
  transition: 0.3s;
  border-radius: 2px;
}

@media (max-width: 768px) {
  .mobile-menu-btn {
    display: flex;
  }
  
  .nav-actions {
    order: -1;
  }
  
  .auth-buttons {
    flex-direction: column;
    gap: 0.25rem;
  }
  
  .btn-auth {
    padding: 0.4rem 1rem;
    font-size: 0.85rem;
  }
  
  .nav-links {
    position: fixed;
    top: 80px;
    left: 0;
    right: 0;
    background-color: white;
    flex-direction: column;
    padding: 2rem;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
    transform: translateY(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
  }
  
  .nav-links-open {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }
  
  .nav-links a {
    padding: 1rem;
    text-align: center;
    border-bottom: 1px solid rgba(24, 45, 79, 0.1);
  }
}
</style>