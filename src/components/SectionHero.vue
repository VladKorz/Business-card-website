<script setup lang="ts">
import ThreeScene from './ThreeScene.vue';
</script>

<template>
  <section id="hero" class="hero-section">
    <div class="hero-content">
      <div class="hero-text">
        <h1>ВЛАДИСЛАВ КОРЗИНКИН</h1>
        <div class="title-line"></div>
        <h2>Специалист по информационным системам & программированию</h2>
        <p>Делай как надо, как не надо не делай</p>
        <div class="hero-cta">
          <a href="#portfolio" class="cta-btn">СМОТРЕТЬ РАБОТЫ</a>
          <a href="#contact" class="cta-btn outline">КОНТАКТЫ</a>
        </div>
      </div>
      <div class="hero-model">
        <ThreeScene />
      </div>
    </div>
    <div class="scroll-indicator">
      <div class="mouse">
        <div class="wheel"></div>
      </div>
      <div class="arrow">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.hero-content {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  height: 100vh;
}

.hero-text {
  flex: 1;
  max-width: 600px;
  z-index: 2;
}

.hero-text h1 {
  font-size: 4rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  letter-spacing: 2px;
}

.title-line {
  width: 100px;
  height: 5px;
  background-color: var(--accent-color);
  margin: 1.5rem 0;
}

.hero-text h2 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  font-weight: 400;
}

.hero-text h2::after {
  display: none;
}

.hero-text p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  line-height: 1.6;
  color: var(--text-secondary);
}

.hero-cta {
  display: flex;
  gap: 1rem;
}

.cta-btn {
  display: inline-block;
  padding: 12px 24px;
  background-color: var(--accent-color);
  color: var(--background-color);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  border: 2px solid var(--accent-color);
}

.cta-btn:hover {
  background-color: transparent;
  color: var(--accent-color);
  text-decoration: none;
}

.cta-btn.outline {
  background-color: transparent;
  color: var(--primary-color);
  border: 2px solid var(--primary-color);
}

.cta-btn.outline:hover {
  background-color: var(--primary-color);
  color: var(--background-color);
}

.hero-model {
  flex: 1;
  height: 500px;
  position: relative;
}

.scroll-indicator {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  animation: fade-in-out 2s infinite;
}

@keyframes fade-in-out {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 1; }
}

.mouse {
  width: 25px;
  height: 45px;
  border: 2px solid var(--primary-color);
  border-radius: 20px;
  position: relative;
  margin-bottom: 10px;
}

.wheel {
  width: 3px;
  height: 8px;
  background-color: var(--primary-color);
  position: absolute;
  top: 7px;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 3px;
  animation: scroll 1.5s infinite;
}

@keyframes scroll {
  0% {
    opacity: 1;
    top: 7px;
  }
  100% {
    opacity: 0;
    top: 30px;
  }
}

.arrow {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.arrow span {
  display: block;
  width: 10px;
  height: 10px;
  border-bottom: 2px solid var(--primary-color);
  border-right: 2px solid var(--primary-color);
  transform: rotate(45deg);
  margin: -5px;
  animation: arrow 2s infinite;
}

.arrow span:nth-child(2) {
  animation-delay: -0.2s;
}

.arrow span:nth-child(3) {
  animation-delay: -0.4s;
}

@keyframes arrow {
  0% {
    opacity: 0;
    transform: rotate(45deg) translate(-5px, -5px);
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    transform: rotate(45deg) translate(5px, 5px);
  }
}

@media (max-width: 992px) {
  .hero-content {
    flex-direction: column;
    text-align: center;
    padding-top: 100px;
  }
  
  .hero-text {
    max-width: 100%;
    margin-bottom: 2rem;
  }
  
  .title-line {
    margin: 1.5rem auto;
  }
  
  .hero-cta {
    justify-content: center;
  }
  
  .hero-model {
    width: 100%;
    max-width: 500px;
  }
}

.small {
  font-size: 0.7rem;
  opacity: 0.7;
  margin-top: 5px;
}

@media (max-width: 768px) {
  .hero-content {
    flex-direction: column;
    text-align: center;
    height: auto;
    padding: 4rem 2rem;
  }

  .hero-text {
    max-width: 100%;
    margin-bottom: 3rem;
  }

  .hero-text h1 {
    font-size: 2.5rem;
  }

  .title-line {
    margin: 1rem auto;
  }

  .hero-text h2 {
    font-size: 1.5rem;
  }

  .hero-text p {
    font-size: 1rem;
  }

  .hero-cta {
    justify-content: center;
  }

  .hero-model {
    height: 300px;
    width: 100%;
  }

  .scroll-indicator {
    display: none;
  }
  
  .model-info {
    bottom: auto;
    top: 20px;
    right: auto;
    left: 50%;
    transform: translateX(-50%);
  }
}

@media (max-width: 480px) {
  .hero-text h1 {
    font-size: 2.5rem;
  }
  
  .hero-cta {
    flex-direction: column;
    gap: 0.5rem;
  }
  
  .hero-model {
    height: 300px;
  }
}
</style>