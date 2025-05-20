<script setup lang="ts">
const achievements = [
  {
    title: 'Премия за лучший 3D портфолио',
    date: '2024',
    description: 'Признание за выдающееся 3D моделирование и веб-интеграцию на Международном фестивале цифрового искусства.'
  },
  {
    title: 'Публикация в WebGL Masters',
    date: '2023',
    description: 'Выбран одним из 20 лучших разработчиков WebGL, расширяющих границы 3D рендеринга в браузере.'
  },
  {
    title: 'Контрибьютор с открытым исходным кодом',
    date: '2022',
    description: 'Значительный вклад в библиотеку Three.js, в частности, оптимизация производительности для сложных 3D сцен.'
  },
  {
    title: 'Более 100K загрузок',
    date: '2021',
    description: 'Создал популярный плагин просмотра 3D моделей для Vue.js с более чем 100 000 загрузок на npm.'
  }
];
</script>

<template>
  <section id="achievements" class="section achievement-section">
    <div class="container">
      <h2>ДОСТИЖЕНИЯ</h2>
      <div class="achievements-grid">
        <div v-for="(achievement, index) in achievements" :key="index" class="achievement-card">
          <div class="achievement-date">{{ achievement.date }}</div>
          <h3 class="achievement-title">{{ achievement.title }}</h3>
          <p class="achievement-description">{{ achievement.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.achievement-section {
  background-color: var(--secondary-bg);
}

.achievements-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 3rem;
}

.achievement-card {
  background-color: var(--background-color);
  padding: 2rem;
  border: 1px solid var(--border-color);
  position: relative;
  transition: transform 0.3s ease, border-color 0.3s ease;
}

.achievement-card:hover {
  transform: translateY(-10px);
  border-color: var(--accent-color);
}

.achievement-date {
  font-size: 0.85rem;
  color: var(--accent-color);
  margin-bottom: 0.5rem;
  font-weight: 700;
}

.achievement-title {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.achievement-description {
  color: var(--text-secondary);
  line-height: 1.6;
}

@media (max-width: 768px) {
  .achievements-grid {
    grid-template-columns: 1fr;
  }
}
</style>