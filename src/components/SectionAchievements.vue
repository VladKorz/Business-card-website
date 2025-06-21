<script setup lang="ts">
const achievements = [
{
    link: '',
    title: 'Окончание колледжа',
    date: 'Июнь 2025',
    description: 'Эх, этого еще не произошло. Но я очень надеюсь что я смогу с гордостью об этом тут написать.'
  },
{
    link: 'https://clck.ru/3MPbmi',
    title: 'Публикация в Яндекс Игры',
    date: 'Август 2024',
    description: 'Я разработал игру "Побег от Фредди!", и ее публикация стала для меня маленькой победой – добиться этого было непросто. К сожалению, через пару месяцев игру удалили из-за низкого спроса. Сейчас в нее можно поиграть только в черновой версии по ссылке ниже.'
  },
  {
    link: 'https://clck.ru/3MPYfW',
    title: 'Разработчик игр на C# в Unity',
    date: 'Май 2024',
    description: 'Успешно освоил дополнительную общеобразовательную программу НОЧУ ВО «Московский финансово-промышленный университет «Синергия» в объеме 144 академических часов. Ссылка на сертификат нижн.'
  },
  
  {
    link: 'https://clck.ru/3MPbjT',
    title: 'Курить, чтобы бросить!',
    date: 'Февраль 2023',
    description: 'Да, я бросил курить. Несмотря на то, что это не профессиональное достижение, оно для меня настолько значимо, что я не могу о нем не сказать. Помогла книга по ссылке ниже.'
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
          <a :href="achievement.link" style="display: block" target="_blank">{{ achievement.link }}</a>
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
-->