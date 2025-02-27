<template>
    <nav class="navbar">
      <div class="logo">Mi Portafolio</div>
      <button class="menu-toggle" @click="toggleMenu">{{ isOpen ? '✖' : '☰' }}</button>
      <ul :class="{ 'nav-links': true, 'open': isOpen }">
        <li v-for="(link, index) in links" :key="index">
          <a :href="link.href" @click="closeMenu">{{ link.text }}</a>
        </li>
      </ul>
    </nav>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isOpen: false,
        links: [
          { text: 'Inicio', href: '#hero' },
          { text: 'Sobre Mí', href: '#sobre-mi' },
          { text: 'Skills', href: '#skills' },
          { text: 'Portafolio', href: '#portfolio' },
          { text: 'Contacto', href: '#contact' }
        ]
      };
    },
    methods: {
      toggleMenu() {
        this.isOpen = !this.isOpen;
      },
      closeMenu() {
        this.isOpen = false;
      }
    }
  };
  </script>
  
  <style scoped>
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 20px;
    background: var(--primario);
    color: white;
  }
  
  .logo {
    font-size: 24px;
    font-weight: bold;
  }
  
  .menu-toggle {
    font-size: 24px;
    background: none;
    border: none;
    color: white;
    cursor: pointer;
    display: none;
  }
  
  .nav-links {
    list-style: none;
    display: flex;
    gap: 20px;
  }
  
  .nav-links li a {
    text-decoration: none;
    color: white;
    font-size: 18px;
    transition: color 0.3s;
  }
  
  .nav-links li a:hover {
    color: var(--secundario);
  }
  
  @media (max-width: 768px) {
    .menu-toggle {
      display: block;
    }
    .nav-links {
      position: absolute;
      top: 60px;
      right: 0;
      background: var(--primario);
      width: 100%;
      flex-direction: column;
      align-items: center;
      padding: 20px 0;
      transform: translateY(-100%);
      transition: transform 0.3s ease-in-out;
    }
    .nav-links.open {
      transform: translateY(0);
    }
  }
  </style>