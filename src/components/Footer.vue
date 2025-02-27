<template>
    <footer class="footer">
      <div class="container">
        <p>&copy; {{ year }} Orlando Escalante. Developer Ⓡ</p>
        
      </div>
    </footer>
  </template>
  
  <script setup>
  const year = new Date().getFullYear();
  </script>
  
  <style scoped>
  .footer {
    background: #111;
    color: white;
    text-align: center;
    padding: 1.5rem 0;
  }
  .container {
    max-width: 900px;
    margin: auto;
  }
  .social-links {
    margin-top: 10px;
  }
  .social-links a {
    color: white;
    margin: 0 10px;
    font-size: 1.5rem;
    transition: 0.3s;
  }
  .social-links a:hover {
    color: #42b883;
  }
  </style>
  