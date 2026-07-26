<script setup>

</script>
<template>
  <div class="galeria">
    <div class="proyectos">
      <img src='/src/assets/ecommerce.jpg.webp' alt='Proyecto E-commerce'>
      <div class="proyecto-info">
        <h3>E-commerce</h3>
        <p>"Plataforma de comercio electrónico con checkout y panel admin; mejoró la conversión un 35% el primer año."</p>
        <div class="proyecto-links">
          <a href="https://E-commerce.com" class="btn-ver-mas" target="_blank" rel="noopener noreferrer">Ver más</a>
          <a href="https//://github.com/GabiJauregui10/E-commerce" class="github-link" target="_blank" rel="noopener noreferrer">
          <img src="/src/assets/github_icon.svg" alt="GitHub" class="github-icon" /></a>
        </div>
      </div>
    </div>
    <div class="proyectos">
      <img src='/src/assets/tareas.jpg.jpg' alt='Proyecto Gestor de Tareas'>
      <div class="proyecto-info">
        <h3>Gestor de Tareas</h3>
        <p>"App para equipos con autenticación JWT, drag & drop y sincronización en tiempo real."</p>
        <div class="proyecto-links">
          <a href="https://GestorDeTareas.com" class="btn-ver-mas" target="_blank" rel="noopener noreferrer">Ver más</a>
          <a href="https//://github.com/GabiJauregui10/GestorDeTareas" class="github-link" target="_blank" rel="noopener noreferrer">
          <img src="/src/assets/github_icon.svg" alt="GitHub" class="github-icon" /></a>
        </div>
      </div>
    </div>
    <div class="proyectos">
      <img src='/src/assets/dashboard1.jpg' alt='Proyecto Dashboard de Ventas'>
      <div class="proyecto-info">
        <h3>Dashboard de Ventas</h3>
        <p>"Dashboard interactivo con filtros y gráficos (Vue + Chart.js) para métricas comerciales."</p>
        <div div class="proyecto-links">
          <a href="https://Dashboard.com" class="btn-ver-mas" target="_blank" rel="noopener noreferrer">Ver más</a>
          <a href="https//://github.com/GabiJauregui10/Dashboard" class="github-link" target="_blank" rel="noopener noreferrer">
          <img src="/src/assets/github_icon.svg" alt="GitHub" class="github-icon" /></a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.galeria {
  width: 100%;
  height: 100%;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  padding: 20px;
  justify-content: center;
  background: linear-gradient(-45deg, #021526, #7fffd4 , #e5e7eb);
  background-size: 400% 400%;
  animation: gradientAnimation 15s ease infinite;
}
@keyframes gradientAnimation {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
.proyectos{
  display: flex;
  flex-direction: column;
  border: 2px solid #0e0101ff;
  border-radius: 8px;
  overflow: hidden;
  background-color: #00c896;
  max-width: 222px;
  flex: 1 1 300px;
}

.proyectos img{
  width: 100%;
  height: auto;
  display: block;
}

.proyecto-info {
  display: flex;
  flex-direction: column;
  justify-content: space-between; /* 🔹 separa el texto del logo */
  align-items: center;
  height: 100%; /* asegura que ocupe todo el alto del card */
  padding: 1rem;
  text-align: center;
  color: #fff;
}


.proyecto-info h3 {
  margin: 10px 0;
  font-size: 1.3em;
  color: #110101ff;
}

.proyecto-info p {
  margin: 10px 0;
  font-size: 1em;
  color: #110101ff;
}

.proyecto-links{
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 10px;

}
.github-link {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  color: #8fffcb; /* color del texto */
  text-decoration: none;
  font-size: 0.9rem;
  transition: color 0.3s, transform 0.3s;
}

.github-link:hover {
  text-decoration: underline;
  transform: translateY(-1px);
}

/* 🔹 Ajuste del logo de GitHub */
.github-link img {
  width: 40px;            /* tamaño equilibrado */
  height: 40px;
  object-fit: contain;
  transition: filter 0.3s;
}

/* 🔹 Efecto al pasar el mouse */
.github-link:hover img {
  filter: invert(100%) brightness(200%); /* se vuelve blanco en hover */
}




</style>
