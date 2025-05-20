<script setup lang="ts">
const skills = [
  { name: 'Спать', level: 99 },
  { name: 'Смотреть сериалы', level: 99 },
  { name: 'Вкусно кушать', level: 99 },
];
</script>

<template>
  <section id="about" class="section">
    <div class="container">
      <h2>ОБО МНЕ</h2>
      <div class="about-content">
        <div class="about-text">
          <p>Я в своем познании настолько преисполнился, что я как будто бы уже

сто триллионов миллиардов лет проживаю на триллионах и

триллионах таких же планет, как эта Земля, мне этот мир абсолютно

понятен, и я здесь ищу только одного - покоя, умиротворения и

вот этой гармонии, от слияния с бесконечно вечным, от созерцания

великого фрактального подобия и от вот этого замечательного всеединства

существа, бесконечно вечного, куда ни посмотри, хоть вглубь - бесконечно

малое, хоть ввысь - бесконечное большое, понимаешь? А ты мне опять со

своим вот этим, иди суетись дальше, это твоё распределение, это

твой путь и твой горизонт познания и ощущения твоей природы, он

несоизмеримо мелок по сравнению с моим, понимаешь?</p>
          
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
  background-color: var(--secondary-bg);
  border-radius: 0;
  overflow: hidden;
  position: relative;
}

.skill-level {
  height: 100%;
  background-color: var(--accent-color);
  position: absolute;
  top: 0;
  left: 0;
  animation: skill-fill 1.5s ease-out forwards;
  width: 0;
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