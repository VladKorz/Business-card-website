<script setup lang="ts">
import { ref, computed } from 'vue';

const categories = ['Все', '3D Модели', 'Веб-разработка', 'UI/UX Дизайн'];
const activeCategory = ref('Все');

const projects = [
  {
    id: 1,
    title: 'Киберпанк персонаж',
    category: '3D Модели',
    image: 'https://images.pexels.com/photos/6330644/pexels-photo-6330644.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
    description: 'Полностью ригнутый 3D персонаж, созданный для независимой игровой студии.'
  },
  {
    id: 2,
    title: 'Панель управления интернет-магазина',
    category: 'Веб-разработка',
    image: 'https://images.pexels.com/photos/6956183/pexels-photo-6956183.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
    description: 'Админ-панель на React с визуализацией данных в реальном времени.'
  },
  {
    id: 3,
    title: 'Интерфейс музыкального приложения',
    category: 'UI/UX Дизайн',
    image: 'https://images.pexels.com/photos/3756766/pexels-photo-3756766.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
    description: 'Музыкальное приложение в темной теме с акцентом на доступность.'
  },
  {
    id: 4,
    title: 'Научно-фантастическая среда',
    category: '3D Модели',
    image: 'https://images.pexels.com/photos/5011647/pexels-photo-5011647.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
    description: 'Футуристическая сцена с процедурными материалами и освещением.'
  },
  {
    id: 5,
    title: 'Трекер криптовалют',
    category: 'Веб-разработка',
    image: 'https://images.pexels.com/photos/844124/pexels-photo-844124.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
    description: 'Приложение для отслеживания криптовалют на Vue.js с интеграцией API в реальном времени.'
  },
  {
    id: 6,
    title: 'Приложение умного дома',
    category: 'UI/UX Дизайн',
    image: 'https://images.pexels.com/photos/4144179/pexels-photo-4144179.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
    description: 'Минималистичный интерфейс для управления системами домашней автоматизации.'
  }
];

const filteredProjects = computed(() => {
  if (activeCategory.value === 'Все') {
    return projects;
  }
  return projects.filter(project => project.category === activeCategory.value);
});

function setCategory(category: string) {
  activeCategory.value = category;
}
</script>

<template>
  <section id="portfolio" class="section">
    <div class="container">
      <h2>ПОРТФОЛИО</h2>
      
      <div class="portfolio-filter">
        <button 
          v-for="category in categories" 
          :key="category"
          :class="['filter-btn', { active: activeCategory === category }]"
          @click="setCategory(category)"
        >
          {{ category }}
        </button>
      </div>
      
      <div class="portfolio-grid">
        <div 
          v-for="project in filteredProjects" 
          :key="project.id"
          class="portfolio-item"
        >
          <div class="portfolio-image">
            <img :src="project.image" :alt="project.title">
            <div class="portfolio-overlay">
              <div class="overlay-content">
                <h3>{{ project.title }}</h3>
                <p>{{ project.description }}</p>
                <a href="#" class="view-project">СМОТРЕТЬ ПРОЕКТ</a>
              </div>
            </div>
          </div>
          <div class="portfolio-info">
            <h3>{{ project.title }}</h3>
            <span class="category">{{ project.category }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.portfolio-filter {
  display: flex;
  justify-content: center;
  margin: 2rem 0 3rem;
  flex-wrap: wrap;
  gap: 1rem;
}

.filter-btn {
  padding: 0.5rem 1.5rem;
  background: transparent;
  border: 1px solid var(--border-color);
  color: var(--text-color);
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.filter-btn:hover,
.filter-btn.active {
  background-color: var(--accent-color);
  color: var(--background-color);
  border-color: var(--accent-color);
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 2rem;
}

.portfolio-item {
  background-color: var(--secondary-bg);
  overflow: hidden;
}

.portfolio-image {
  position: relative;
  overflow: hidden;
  height: 250px;
}

.portfolio-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.portfolio-item:hover .portfolio-image img {
  transform: scale(1.1);
}

.portfolio-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(10, 10, 10, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
  padding: 1.5rem;
}

.portfolio-item:hover .portfolio-overlay {
  opacity: 1;
}

.overlay-content {
  text-align: center;
}

.overlay-content h3 {
  margin-bottom: 0.75rem;
  font-size: 1.5rem;
}

.overlay-content p {
  margin-bottom: 1.5rem;
  color: var(--text-secondary);
}

.view-project {
  display: inline-block;
  padding: 0.6rem 1.2rem;
  background-color: var(--accent-color);
  color: var(--background-color);
  text-transform: uppercase;
  font-size: 0.8rem;
  letter-spacing: 1px;
  font-weight: 700;
  transition: all 0.3s ease;
}

.view-project:hover {
  background-color: var(--primary-color);
  text-decoration: none;
}

.portfolio-info {
  padding: 1.5rem;
}

.portfolio-info h3 {
  margin-bottom: 0.5rem;
  font-size: 1.2rem;
}

.category {
  color: var(--accent-color);
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 1px;
}

@media (max-width: 768px) {
  .portfolio-grid {
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  }
}

@media (max-width: 480px) {
  .portfolio-grid {
    grid-template-columns: 1fr;
  }
}
</style>