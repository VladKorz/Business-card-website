<script setup lang="ts">
const currentYear = new Date().getFullYear();
</script>

<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-logo">
          <h3>VladKorz</h3>
          <p>Возьмите меня на работу.</p>
        </div>
        
        <div class="footer-links">
          <div class="footer-col">
            <h4>НАВИГАЦИЯ</h4>
            <ul>
              <li><a href="#hero">Главная</a></li>
              <li><a href="#about">Обо мне</a></li>
              <li><a href="#achievements">Достижения</a></li>
              <li><a href="#portfolio">Портфолио</a></li>
              <li><a href="#contact">Контакты</a></li>
            </ul>
          </div>
          
          <div class="footer-col">
            <h4>СОЦИАЛЬНЫЕ СЕТИ</h4>
            <ul>
              <li><a href="https://github.com/VladKorz" target="_blank">GitHub</a></li>
            </ul>
          </div>
        </div>
      </div>
      
      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} Владислав Корзинкин. Все права защищены. Но это не точно.</p>
        <a href="#hero" class="back-to-top">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M12 19V5M5 12l7-7 7 7"/>
          </svg>
        </a>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: var(--background-color);
  padding: 5rem 0 2rem;
  border-top: 1px solid var(--border-color);
}

.footer-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  margin-bottom: 3rem;
}

.footer-logo h3 {
  font-size: 1.8rem;
  margin-bottom: 1rem;
  font-family: "Roboto Mono", monospace;
  letter-spacing: 2px;
}

.footer-logo p {
  color: var(--text-secondary);
  max-width: 80%;
  line-height: 1.7;
}

.footer-links {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

.footer-col h4 {
  font-size: 1rem;
  margin-bottom: 1.5rem;
  position: relative;
  display: inline-block;
}

.footer-col h4::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -5px;
  width: 100%;
  height: 2px;
  background-color: var(--accent-color);
}

.footer-col ul {
  list-style: none;
  padding: 0;
}

.footer-col li {
  margin-bottom: 0.75rem;
}

.footer-col a {
  color: var(--text-secondary);
  transition: color 0.3s ease;
}

.footer-col a:hover {
  color: var(--accent-color);
  text-decoration: none;
}

.footer-bottom {
  border-top: 1px solid var(--border-color);
  padding-top: 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: var(--text-secondary);
  font-size: 0.9rem;
}

.back-to-top {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background-color: var(--secondary-bg);
  border: 1px solid var(--border-color);
  color: var(--text-color);
  transition: all 0.3s ease;
}

.back-to-top:hover {
  background-color: var(--accent-color);
  color: var(--background-color);
  border-color: var(--accent-color);
}

@media (max-width: 992px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 3rem;
  }
  
  .footer-logo p {
    max-width: 100%;
  }
}

@media (max-width: 768px) {
  .footer-links {
    grid-template-columns: 1fr;
  }
  
  .footer-bottom {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }
}
</style>