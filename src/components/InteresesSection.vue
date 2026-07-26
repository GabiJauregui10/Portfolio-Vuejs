<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'


const intereses = ref([
  '💻 Open Source & Comunidad Dev: Me gusta colaborar en proyectos de código abierto en GitHub, compartiendo ideas y aprendiendo de otros desarrolladores.',
  '⚽ Deportes: El fútbol es mi actividad preferida para desconectarme del código, mantenerme activo y potenciar el trabajo en equipo.',
  '🚀 Innovación & Tecnología: Siempre estoy explorando nuevas tendencias — IA, apps móviles y frameworks modernos — buscando cómo integrarlas en proyectos reales.',
  '🎮 Videojuegos: Los videojuegos me inspiran a pensar de forma creativa y estratégica; además, alimentan mi interés por el diseño, la lógica y la experiencia del usuario.',
])

let io // IntersectionObserver

onMounted(() => {
  const items = document.querySelectorAll('.intereses .item')
  io = new IntersectionObserver(
    entries => {
      entries.forEach(e => {
        if (e.isIntersecting) e.target.classList.add('reveal')
      })
    },
    { rootMargin: '0px 0px -10% 0px', threshold: 0.15 }
  )

  items.forEach((el, i) => {
    el.style.setProperty('--i', i) // delay escalonado
    el.classList.toggle('alt', i % 2 === 1) // alterna entrada
    io.observe(el)
  })
})

onBeforeUnmount(() => {
  if (io) io.disconnect()
})
</script>

<template>
  <section class="intereses" id="intereses" aria-labelledby="intereses-title">
    <FondoLava />

    <div class="card">
      <h2 id="intereses-title">Mis pasatiempos</h2>

      <ul class="contenedor-lista">
        <li class="item" v-for="interes in intereses" :key="interes">
          {{ interes }}
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
/* ===== Contenedor general ===== */
.intereses{
  position: relative;
  max-width: 900px;
  margin: 2rem auto;
  padding: .25rem;
  z-index: 1;
}

/* Tarjeta con glass suave, coherente con tu UI */
.card{
  position: relative;
  padding: 2rem 1.5rem;
  background: rgba(22,22,22,.85);           /* similar a tus cards */
  border: 1px solid rgba(127,255,212,.15);  /* --line */
  border-radius: 16px;
  box-shadow: 0 10px 20px rgba(0,0,0,.35);
  backdrop-filter: blur(10px);
  overflow: hidden;
}

/* Glow sutil interno que combina con tu timeline */
.card::before{
  content:"";
  position: absolute; inset: 0;
  background: radial-gradient(600px 300px at 12% 20%, rgba(127,255,212,.08), transparent 60%);
  filter: blur(22px);
  pointer-events: none;
}

/* Hover suavito para la tarjeta */
.card:hover{
  border-color: var(--line-soft);
    box-shadow:
      0 0 25px rgba(127,255,212,.15),
      0 0 40px rgba(127,255,212,.10),
      0 12px 28px rgba(0,0,0,.35);
  }
  </style>
