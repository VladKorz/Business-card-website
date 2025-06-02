<script setup lang="ts">
const skills = [
  { name: 'Разработка кода ИС', level: 70 },
  { name: 'Проектирование и дизайн ИС', level: 60 },
  { name: 'Тестирование ИС', level: 75 },
  { name: 'Компьютерные сети', level: 49 },
  { name: 'Базы данных', level: 60 },
  { name: 'Управление проектами', level: 90 },
  { name: 'Сборка и ремонт ПК', level: 90 },
  { name: 'Настройка и работа с ОС Windows и Linux', level: 70 },
  { name: 'C# Unity', level: 90 },
];
</script>

<template>
  <section id="about" class="section">
    <div class="container">
      <h2>ОБО МНЕ</h2>
      <div class="about-content">
        <div class="about-text">
          <p>Я начинающий специалист , который стремится к самосовершенствованию и постоянно расширяет свои навыки в области разработки и проектирования информационных систем. Моя цель - стать профессиональным разработчиком, который сможет создавать эффективные и инновационные решения для различных отраслей бизнеса.</p>  
          <P>Имя: Владислав</P>
          <p>Образование: Cреднее специальное, 2025, МФПУ «Синергия», Москва, Информационные системы и программирование</p>
          <P>Родился: 27 февраля 2006</P>
          <div class="about-cta">
            <a href="#portfolio" class="about-btn">СМОТРЕТЬ РАБОТЫ</a>
            <a href="/resume.pdf" target="_blank" class="about-btn outline">СКАЧАТЬ РЕЗЮМЕ</a>
          </div>
        </div>
        
        <div class="skills">
          <h3>НАВЫКИ</h3>
          <div class="skill-bars">
            <div v-for="skill in skills" :key="skill.name" class="skill-item">
              <div class="skill-info">
                <span class="skill-name">{{ skill.name }}</span>
                <span class="skill-percentage">{{ skill.level }}%</span>
              </div>
              <div class="skill-bar">
                <div class="skill-level" :style="{ width: `${skill.level}%` }"></div>
              </div>
            </div>
          </div>
          <h4>!Процент освоения — субъективная оценка!</h4>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  margin-top: 2rem;
}

.about-text p {
  margin-bottom: 1.5rem;
  font-size: 1.1rem;
  line-height: 1.7;
}

.about-cta {
  margin-top: 2rem;
  display: flex;
  gap: 1rem;
}

.about-btn {
  display: inline-block;
  padding: 10px 20px;
  background-color: var(--accent-color);
  color: var(--background-color);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 0.85rem;
  transition: all 0.3s ease;
  border: 2px solid var(--accent-color);
}

.about-btn:hover {
  background-color: transparent;
  color: var(--accent-color);
  text-decoration: none;
}

.about-btn.outline {
  background-color: transparent;
  color: var(--primary-color);
  border: 2px solid var(--primary-color);
}

.about-btn.outline:hover {
  background-color: var(--primary-color);
  color: var(--background-color);
}

.skills h3 {
  margin-bottom: 1.5rem;
  font-size: 1.5rem;
  position: relative;
  display: inline-block;
}

.skills h4 {
  margin-top: 1rem;
  font-size: 1rem;
  position: relative;
  display: inline-block;
}

.skills h3::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -5px;
  width: 100%;
  height: 3px;
  background-color: var(--accent-color);
}

.skill-bars {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.skill-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
}

.skill-name {
  font-weight: 600;
  text-transform: uppercase;
  font-size: 0.85rem;
  letter-spacing: 1px;
}

.skill-percentage {
  color: var(--accent-color);
  font-weight: 700;
}

.skill-bar {
  height: 10px;
  width: 100%;
  background-color: var(--secondary-bg);
  border-radius: 5px;
  overflow: hidden;
}

.skill-level {
  height: 100%;
  background-color: var(--accent-color);
  transition: width 0.8s ease-out;
  border-radius: 5px;
}

@keyframes skill-fill {
  from {
    width: 0;
  }
  to {
    width: var(--width);
  }
}

@media (max-width: 992px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 3rem;
  }
}

@media (max-width: 768px) {
  .about-cta {
    flex-direction: column;
    gap: 0.75rem;
  }
  
  .about-btn {
    width: 100%;
    text-align: center;
  }
}
</style>