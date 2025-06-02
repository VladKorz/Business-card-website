<script setup lang="ts">

// Contact information
const contactInfo = {
  phone: '+7 903 541 06 86',
  email: 'chiloviksgon@gmail.com',
  telegram: '@VlaDik16000',
  github: 'VladKorz'
};

</script>

<template>
  <section id="contact" class="section contact-section">
    <div class="container">
      <h2>КОНТАКТЫ</h2>
      
      <div class="contact-content">
        <div class="contact-info">
          <h3>СВЯЗАТЬСЯ СО МНОЙ</h3>
          <p>Не стесняйтесь обращаться для сотрудничества, обсуждения проектов или просто поздороваться. Я всегда открыт для общения.</p>
          
          <div class="info-items">
            <div class="info-item">
              <div class="info-icon">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path>
                </svg>
              </div>
              <div class="info-text">
                <span>Телефон</span>
                <a :href="`tel:${contactInfo.phone}`">{{ contactInfo.phone }}</a>
              </div>
            </div>
            
            <div class="info-item">
              <div class="info-icon">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path>
                  <polyline points="22,6 12,13 2,6"></polyline>
                </svg>
              </div>
              <div class="info-text">
                <span>Email</span>
                <a :href="`mailto:${contactInfo.email}`">{{ contactInfo.email }}</a>
              </div>
            </div>
            
            <div class="info-item">
              <div class="info-icon">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M21.58 11.4a9.25 9.25 0 0 1-4.17 5.44A9.34 9.34 0 0 1 12 17.94a9.24 9.24 0 0 1-5.4-1.1A9.26 9.26 0 0 1 2.42 11.4"></path>
                  <path d="M13.5 6.5l2.5 2.5-2.5 2.5"></path>
                  <path d="M10.5 6.5l-2.5 2.5 2.5 2.5"></path>
                  <path d="M12 20v-4"></path>
                  <path d="M12 6V2"></path>
                </svg>
              </div>
              <div class="info-text">
                <span>GitHub</span>
                <a :href="`https://github.com/${contactInfo.github}`" target="_blank">github.com/{{ contactInfo.github }}</a>
              </div>
            </div>
            
            <div class="info-item">
              <div class="info-icon">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M21.5 4.5L2.5 12.5L21.5 20.5V4.5Z"></path>
                  <path d="M12 12.5L2.5 12.5"></path>
                  <path d="M12 12.5L16.5.5 12 12.5Z"></path>
                </svg>
              </div>
              <div class="info-text">
                <span>Telegram</span>
                <a :href="`https://t.me/${contactInfo.telegram.substring(1)}`" target="_blank">{{ contactInfo.telegram }}</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  background-color: var(--secondary-bg);
  padding: 6rem 0;
}

.contact-content {
  max-width: 800px;
  margin: 3rem auto 0;
}

.contact-info h3 {
  margin-bottom: 1.5rem;
  font-size: 1.5rem;
  position: relative;
  display: inline-block;
}

.contact-info h3::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -5px;
  width: 100%;
  height: 3px;
  background-color: var(--accent-color);
}

.contact-info p {
  margin-bottom: 3rem;
  line-height: 1.7;
  font-size: 1.1rem;
  color: var(--text-secondary);
}

.info-items {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
}

.info-item {
  display: flex;
  align-items: flex-start;
  background-color: var(--background-color);
  padding: 1.5rem;
  border-radius: 8px;
  transition: transform 0.3s ease;
}

.info-item:hover {
  transform: translateY(-5px);
}

.info-icon {
  margin-right: 1rem;
  color: var(--accent-color);
}

.info-text {
  display: flex;
  flex-direction: column;
}

.info-text span {
  font-size: 0.85rem;
  color: var(--text-secondary);
  margin-bottom: 0.25rem;
}

.info-text a {
  color: var(--text-color);
  transition: color 0.3s ease;
  font-size: 1.1rem;
}

.info-text a:hover {
  color: var(--accent-color);
}

@media (max-width: 768px) {
  .info-items {
    grid-template-columns: 1fr;
  }
  
  .contact-info p {
    font-size: 1rem;
  }
}

.contact-form {
  margin-bottom: 3rem;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 1rem;
  border: 2px solid var(--border-color);
  border-radius: 8px;
  background-color: var(--background-color);
  color: var(--text-color);
  font-size: 1rem;
  transition: border-color 0.3s ease;
}

.form-group textarea {
  min-height: 150px;
  resize: vertical;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--accent-color);
}

button[type="submit"] {
  background-color: var(--accent-color);
  color: white;
  padding: 1rem 2rem;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button[type="submit"]:hover {
  background-color: var(--accent-color-hover);
}

button[type="submit"]:disabled {
  background-color: var(--text-secondary);
  cursor: not-allowed;
}

.success-message {
  color: #4CAF50;
  margin-top: 1rem;
}

.error-message {
  color: #f44336;
  margin-top: 1rem;
}
</style>