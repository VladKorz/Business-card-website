<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const links = [
  { name: 'ГЛАВНАЯ', href: '#hero' },
  { name: 'ОБО МНЕ', href: '#about' },
  //{ name: 'ДОСТИЖЕНИЯ', href: '#achievements' },
  { name: 'ПОРТФОЛИО', href: '#portfolio' },
  { name: 'КОНТАКТЫ', href: '#contact' }
];

const isMenuOpen = ref(false);
const isScrolled = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
  if (isMenuOpen.value) {
    document.body.style.overflow = 'hidden';
  } else {
    document.body.style.overflow = '';
  }
};

const closeMenu = () => {
  isMenuOpen.value = false;
  document.body.style.overflow = '';
};

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
  <nav :class="['navbar', { 'scrolled': isScrolled }]">
    <div class="navbar-container">
      <a href="#" class="logo">VladKorz</a>
      
      <div class="menu-toggle" @click="toggleMenu">
        <div :class="['bar', { 'active': isMenuOpen }]"></div>
        <div :class="['bar', { 'active': isMenuOpen }]"></div>
        <div :class="['bar', { 'active': isMenuOpen }]"></div>
      </div>
      
      <ul :class="['nav-menu', { 'active': isMenuOpen }]">
        <li v-for="link in links" :key="link.name" class="nav-item">
          <a :href="link.href" class="nav-link" @click="closeMenu">{{ link.name }}</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  transition: background-color 0.3s ease, padding 0.3s ease;
  padding: 1.5rem 0;
  background-color: rgba(10, 10, 10, 0.8);
  backdrop-filter: blur(10px);
}

.navbar.scrolled {
  background-color: var(--background-color);
  padding: 1rem 0;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
}

.navbar-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary-color);
  font-family: "Roboto Mono", monospace;
  letter-spacing: 2px;
  text-decoration: none;
}

.nav-menu {
  display: flex;
  list-style: none;
  margin: 0;
}

.nav-item {
  margin-left: 2rem;
}

.nav-link {
  color: var(--primary-color);
  font-weight: 500;
  text-decoration: none;
  font-size: 0.85rem;
  letter-spacing: 1px;
  position: relative;
  padding: 0.5rem 0;
}

.nav-link::after {
  content: '';
  position: absolute;
  width: 0;
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: var(--accent-color);
  transition: width 0.3s ease;
}

.nav-link:hover::after {
  width: 100%;
}

.menu-toggle {
  display: none;
  cursor: pointer;
}

.bar {
  width: 25px;
  height: 3px;
  background-color: var(--primary-color);
  margin: 5px 0;
  transition: 0.4s;
}

@media (max-width: 768px) {
  .menu-toggle {
    display: block;
    z-index: 1001;
  }
  
  .nav-menu {
    position: fixed;
    left: -100%;
    top: 0;
    flex-direction: column;
    background-color: var(--background-color);
    width: 100%;
    height: 100vh;
    text-align: center;
    transition: 0.5s;
    padding-top: 100px;
  }
  
  .nav-menu.active {
    left: 0;
  }
  
  .nav-item {
    margin: 1.5rem 0;
  }
  
  .bar.active:nth-child(1) {
    transform: translateY(8px) rotate(45deg);
  }
  
  .bar.active:nth-child(2) {
    opacity: 0;
  }
  
  .bar.active:nth-child(3) {
    transform: translateY(-8px) rotate(-45deg);
  }
}
</style>