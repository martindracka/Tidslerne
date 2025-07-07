<script setup lang="ts">
</script>

<template>
  <section class="contact">
    <div class="container">
      <div class="contact-header">
        <h1 class="section-title">Kontakt Os</h1>
        <p class="contact-subtitle">
          Vi er her for at hjælpe dig. Kontakt os i dag for at få svar på dine spørgsmål.
        </p>
      </div>
      
      <div class="contact-content">
        <div class="organization-card">
          <h3>Tidslerne Kræftforening</h3>
          <div class="org-details">
            <p><strong>Att.:</strong> Mai Nielsen, formand</p>
            <div class="address">
              <p>Ådalsparken 29</p>
              <p>6710 Esbjerg V</p>
            </div>
            <div class="contact-methods">
              <p><strong>T:</strong> 86 11 32 44</p>
              <p><strong>M:</strong> 40 15 90 11</p>
            </div>
            <p><strong>CVR:</strong> 17420291</p>
          </div>
        </div>

        <div class="phone-info-card">
          <div class="phone-icon">
            <svg width="60" height="60" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M6.62 10.79C8.06 13.62 10.38 15.94 13.21 17.38L15.41 15.18C15.69 14.9 16.08 14.82 16.43 14.93C17.55 15.3 18.75 15.5 20 15.5C20.55 15.5 21 15.95 21 16.5V20C21 20.55 20.55 21 20 21C10.61 21 3 13.39 3 4C3 3.45 3.45 3 4 3H7.5C8.05 3 8.5 3.45 8.5 4C8.5 5.25 8.7 6.45 9.07 7.57C9.18 7.92 9.1 8.31 8.82 8.59L6.62 10.79Z" fill="white"/>
            </svg>
          </div>
          <h2>Telefon 7020 0515</h2>
          <div class="phone-hours">
            <h3>Telefonerne er åbne i følgende tider:</h3>
            <div class="hours-list">
              <div class="hour-item">
                <span class="day">Mandag:</span>
                <span class="time">18:00 - 20:00</span>
              </div>
              <div class="hour-item">
                <span class="day">Tirsdag:</span>
                <span class="time">10:00 - 12:00</span>
              </div>
              <div class="hour-item">
                <span class="day">Onsdag:</span>
                <span class="time">10:00 - 12:00</span>
              </div>
              <div class="hour-item">
                <span class="day">Torsdag:</span>
                <span class="time">10:00 - 12:00</span>
              </div>
            </div>
          </div>
        </div>

        <div class="info-card primary">
          <div class="info-icon">
            <svg width="40" height="40" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M20 4H4C2.9 4 2.01 4.9 2.01 6L2 18C2 19.1 2.9 20 4 20H20C21.1 20 22 19.1 22 18V6C22 4.9 21.1 4 20 4ZM20 8L12 13L4 8V6L12 11L20 6V8Z" fill="white"/>
            </svg>
          </div>
          <div>
            <h3>Kontakt vedr. medlemsdatabase</h3>
            <p>Send en email til:<br><strong>sekretariat@tidslerne.dk</strong></p>
          </div>
        </div>
        
        <div class="info-card secondary">
          <div class="info-icon">
            <svg width="40" height="40" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M19 14V6C19 5.45 18.55 5 18 5H6C5.45 5 5 5.45 5 6V14C5 14.55 5.45 15 6 15H18C18.55 15 19 14.55 19 14ZM14 6L12 8L10 6H14ZM6 7L8 9L6 11V7ZM18 7V11L16 9L18 7ZM10 18H14V20H10V18Z" fill="white"/>
            </svg>
          </div>
          <div>
            <h3>Fakturaer - regninger</h3>
            <p>Send til:<br><strong>kasserer@tidslerne.dk</strong></p>
          </div>
        </div>
        
        <div class="payment-card">
          <h3>Indbetalinger</h3>
          
          <div class="payment-section">
            <h4>Medlemskontingent:</h4>
            <div class="bank-details">
              <p><strong>Reg. nr:</strong> 9570</p>
              <p><strong>Konto:</strong> 997 0118</p>
              <p><strong>IBAN:</strong> DK1730000009970118</p>
              <p><strong>BIC (SWIFT):</strong> DABADKKK</p>
            </div>
          </div>
          
          <div class="payment-section">
            <h4>Gaver & Donationer (helst via MobilePay):</h4>
            <div class="mobilepay">
              <p><strong>MobilePay:</strong> 211 600</p>
            </div>
            <div class="bank-alternative">
              <p><strong>eller Danske Bank:</strong></p>
              <div class="bank-details">
                <p><strong>Reg. nr:</strong> 9570</p>
                <p><strong>Konto:</strong> 1202 5041</p>
                <p><strong>IBAN:</strong> DK2930000012025041</p>
                <p><strong>BIC (SWIFT):</strong> DABADKKK</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact {
  padding: 6rem 0 4rem;
  background: linear-gradient(135deg, #f8f9fa 0%, rgba(39, 195, 131, 0.05) 100%);
  min-height: 100vh;
}

.contact-header {
  text-align: center;
  margin-bottom: 4rem;
}

.contact-subtitle {
  font-size: 1.2rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}

.contact-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3rem;
  max-width: 800px;
  margin: 0 auto;
}

.organization-card {
  background: linear-gradient(135deg, #A7105A, #27C383);
  color: white;
  padding: 3rem;
  border-radius: 20px;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
  text-align: center;
  width: 100%;
  max-width: 600px;
}

.organization-card h3 {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 2rem;
}

.org-details {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  font-size: 1.1rem;
}

.address {
  border-left: 3px solid rgba(255, 255, 255, 0.3);
  padding-left: 1.5rem;
  margin: 0 auto;
  display: inline-block;
}

.contact-methods {
  background: rgba(255, 255, 255, 0.15);
  padding: 1.5rem;
  border-radius: 10px;
  backdrop-filter: blur(10px);
}

.phone-info-card {
  background: linear-gradient(135deg, #182D4F, #1e3558);
  color: white;
  padding: 4rem 3rem;
  border-radius: 20px;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
  text-align: center;
  width: 100%;
  max-width: 600px;
  transition: transform 0.3s ease;
}

.phone-info-card:hover {
  transform: translateY(-5px);
}

.phone-icon {
  margin-bottom: 2rem;
  display: flex;
  justify-content: center;
  background: rgba(255, 255, 255, 0.1);
  width: 80px;
  height: 80px;
  border-radius: 50%;
  align-items: center;
  margin-left: auto;
  margin-right: auto;
}

.phone-info-card h2 {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 2rem;
  color: #27C383;
}

.phone-hours h3 {
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  opacity: 0.95;
}

.hours-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.hour-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 1.5rem;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 10px;
  border-left: 4px solid #27C383;
  backdrop-filter: blur(10px);
}

.hour-item .day {
  font-weight: 600;
  font-size: 1.1rem;
}

.hour-item .time {
  font-weight: 700;
  color: #27C383;
  font-size: 1.1rem;
}

.info-card {
  background: white;
  padding: 2.5rem;
  border-radius: 15px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  display: flex;
  align-items: flex-start;
  gap: 1.5rem;
  width: 100%;
  max-width: 600px;
  border-left: 4px solid;
}

.info-card.primary {
  border-left-color: #A7105A;
}

.info-card.secondary {
  border-left-color: #27C383;
}

.info-card:hover {
  transform: translateY(-5px);
}

.info-icon {
  flex-shrink: 0;
  padding: 1rem;
  border-radius: 50%;
  color: white;
}

.info-card.primary .info-icon {
  background: linear-gradient(135deg, #A7105A, #d41a6b);
}

.info-card.secondary .info-icon {
  background: linear-gradient(135deg, #27C383, #2dd492);
}

.info-card h3 {
  color: #182D4F;
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
}

.info-card p {
  color: #666;
  line-height: 1.6;
  margin: 0;
  font-size: 1.05rem;
}

.payment-card {
  background: white;
  padding: 3rem;
  border-radius: 20px;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  width: 100%;
  max-width: 600px;
}

.payment-card:hover {
  transform: translateY(-5px);
}

.payment-card h3 {
  color: #182D4F;
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 2rem;
  text-align: center;
  border-bottom: 3px solid #27C383;
  padding-bottom: 1rem;
}

.payment-section {
  margin-bottom: 2.5rem;
}

.payment-section h4 {
  color: #A7105A;
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 1rem;
  text-align: center;
}

.bank-details {
  background: #f8f9fa;
  padding: 1.5rem;
  border-radius: 10px;
  border-left: 4px solid #27C383;
  text-align: center;
}

.bank-details p {
  margin: 0.5rem 0;
  color: #182D4F;
  font-size: 1rem;
  font-weight: 500;
}

.mobilepay {
  background: linear-gradient(135deg, #A7105A, #27C383);
  color: white;
  padding: 1.5rem;
  border-radius: 10px;
  margin-bottom: 1.5rem;
  text-align: center;
}

.mobilepay p {
  margin: 0;
  font-weight: 700;
  font-size: 1.3rem;
}

.bank-alternative {
  margin-top: 1.5rem;
}

.bank-alternative > p {
  color: #666;
  margin-bottom: 1rem;
  font-style: italic;
  text-align: center;
  font-weight: 600;
}

@media (max-width: 768px) {
  .contact-content {
    padding: 0 1rem;
  }
  
  .organization-card {
    padding: 2.5rem 2rem;
  }
  
  .organization-card h3 {
    font-size: 1.5rem;
  }
  
  .phone-info-card {
    padding: 3rem 2rem;
  }
  
  .phone-info-card h2 {
    font-size: 2rem;
  }
  
  .hour-item {
    flex-direction: column;
    gap: 0.5rem;
    text-align: center;
  }
  
  .info-card {
    flex-direction: column;
    text-align: center;
    padding: 2rem;
  }
  
  .payment-card {
    padding: 2.5rem 2rem;
  }
  
  .payment-card h3 {
    font-size: 1.5rem;
  }
}

@media (max-width: 480px) {
  .hour-item .day,
  .hour-item .time {
    font-size: 1rem;
  }
  
  .phone-info-card h2 {
    font-size: 1.8rem;
  }
  
  .organization-card h3 {
    font-size: 1.3rem;
  }
}
</style>