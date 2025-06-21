<script setup lang="ts">
import { ref, computed } from 'vue';

const categories = ['Все', 'Пет-проект', 'Учебный проект', 'Игра', 'Сборка и настройка ЭВМ'];
const activeCategory = ref('Все');

const projects = [
  {
    a: 1,
    id: 1,
    title: 'Окуп баньки',
    category: 'Пет-проект',
    image: 'assets/pet.pro.jpg',
    description: 'Это простое веб-приложение на Vue с БД для отслеживания доходов/расходов бани и расчета ее окупаемости.',
    link: 'https://github.com/VladKorz/BANY_OKUP'
  },
  {
    a: 1,
    id: 2,
    title: 'ВКР',
    category: 'Учебный проект',
    image: 'assets/diplom.jpg',
    description: 'Это проектное решение моей выпускной квалификационной работы. Для ознакомления с проектом рекомендуется начать с презентации.',
    link: 'https://github.com/VladKorz/diplom'
  },
  {
    a: 1,
    id: 3,
    title: 'Business-card-website',
    category: 'Пет-проект',
    image: 'assets/BC.jpg',
    description: 'Собственно, вы сейчас изучаете этот проект в реальном времени.',
    link: 'https://github.com/VladKorz/Business-card-website'
  },
  {
    a: 1,
    id: 4,
    title: 'Побег от Фредди!',
    category: 'Игра',
    image: 'assets/image.png',
    description: 'Эту игру получилось опубликовать в Яндекс Игры. Но ее удалили из-за низкого спроса. Сейчас в нее можно поиграть только в черновике.',
    link: 'https://clck.ru/3MPbmi'
  },
  {
    a: 1,
    id: 5,
    title: 'Ohota Na NextBota',
    category: 'Игра',
    image: 'assets/ohota.jpg',
    description: 'Это весёлый шутер, который у меня не получилось закончить.',
    link: 'https://github.com/VladKorz/OhotaNaNextBota'
  },
  {
    a: 0,
    id: 6,
    title: 'Влад gpt',
    category: 'Пет-проект',
    image: 'assets/gpt.jpg',
    description: 'Это проект, который не был завершён в полной мере. Изначально его планировали сделать общедоступным и коммерчески успешным, но в итоге он распространился лишь в узком кругу пользователей и на бесплатной основе.',
    link: ''
  },
  {
    a: 0,
    id: 7,
    title: 'Ферма на GPU',
    category: 'Сборка и настройка ЭВМ',
    image: 'assets/mf.jpg',
    description: 'Сборка майнинг фермы на GPU. Даа, я и таким занимался. Самое увлекательное в этом проекте было разбираться с сетевыми и другими настройками в терминале RaveOS.',
    link: ''
  },
    {
    a: 0,
    id: 8,
    title: 'Сборка ПК',
    category: 'Сборка и настройка ЭВМ',
    image: 'assets/pc.jpg',
    description: 'Я собирал компы на заказ. Конкретно этот на Хеоn Е5 2643v4, 16 гб ddr4 и 2060 super.',
    link: ''
  },
    {
    a: 1,
    id: 9,
    title: 'Курсовая по УАБД',
    category: 'Учебный проект',
    image: 'assets/db.jpg',
    description: 'Сейчас, с высоты моего опыта, я не считаю эту работу выдающейся, но в своё время она значительно углубила моё понимание темы.',
    link: 'https://drive.google.com/file/d/1-mJDjrksUgxAZXbeGBD1B2j_7CyTLEGo/view?usp=drive_link'
  },
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
      <H3>Здесь представлены мои наиболее значимые проекты.</H3>
      
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
                <a 
                  v-if="project.a === 1"
                  :href="project.link" 
                  target="_blank" 
                  rel="noopener" 
                  class="view-project"
                >
                  СМОТРЕТЬ ПРОЕКТ
                </a>
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