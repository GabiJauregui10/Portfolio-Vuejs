
<script setup>
import { ref } from 'vue'

defineOptions({ name: 'EducacionSection' })

// Línea de tiempo inventada (podés editar libremente)
const items = ref([
  {
    id: 1,
    fecha: '2019',
    titulo: 'Algoritmos y Lógica',
    institucion: 'Curso online (40 h)',
    descripcion: 'Introducción con PSeInt y resolución de problemas.',
    skills: ['variables', 'condicionales', 'bucles']
  },
  {
    id: 2,
    fecha: '2020',
    titulo: 'Python Inicial',
    institucion: 'Autodidacta',
    descripcion: 'Sintaxis, colecciones, funciones y archivos.',
    skills: ['Python', 'pip', 'venv']
  },
  {
    id: 3,
    fecha: '2021',
    titulo: 'Java & POO',
    institucion: 'UTN (Tecnicatura en Programación)',
    descripcion: 'Clases, objetos, encapsulamiento y constructores.',
    skills: ['Java', 'POO', 'UML']
  },
  {
    id: 4,
    fecha: '2022',
    titulo: 'Estructuras de Datos',
    institucion: 'UTN',
    descripcion: 'Listas, pilas, colas, árboles y complejidad Big-O.',
    skills: ['Listas', 'Árboles', 'Algoritmos']
  },
  {
    id: 5,
    fecha: '2023',
    titulo: 'Desarrollo Web',
    institucion: 'FreeCodeCamp + proyectos',
    descripcion: 'HTML5, CSS3, DOM y responsive design.',
    skills: ['HTML', 'CSS', 'JavaScript']
  },
  {
    id: 6,
    fecha: '2024',
    titulo: 'Control de versiones',
    institucion: 'Proyectos personales',
    descripcion: 'Git, GitHub, ramas, issues y pull requests.',
    skills: ['Git', 'GitHub', 'Gitflow']
  },
  {
    id: 7,
    fecha: '2025 (en curso)',
    titulo: 'Frontend con Vue 3',
    institucion: 'Portafolio ALT+F4',
    descripcion: 'Vite, componentes, props y eventos.',
    skills: ['Vue 3', 'Vite', 'Componentes'],
    estado: 'En curso'
  }
])
</script>

<template>
  <section class="timeline">
    <h2>Mi formación en programación</h2>

    <ol class="timeline-list">
      <!-- agrega el índice para el "stagger" y lo pasamos a CSS con --i -->
      <li
        v-for="(i, idx) in items"
        :key="i.id"
        class="timeline-item"
        :style="{ '--i': idx }"
      >
        <div class="dot" aria-hidden="true"></div>
        <time class="date">{{ i.fecha }}</time>

        <div class="card">
          <h3 class="title">{{ i.titulo }}</h3>
          <p class="inst">{{ i.institucion }}</p>
          <p class="desc">{{ i.descripcion }}</p>

          <ul v-if="i.skills?.length" class="chips">
            <li v-for="(s, idx) in i.skills" :key="idx">{{ s }}</li>
          </ul>

          <span v-if="i.estado" class="badge">{{ i.estado }}</span>
        </div>
      </li>
    </ol>
  </section>
</template>

<style >
:root{
  --card:#161616;
  --text:#EDEDED;
  --muted:#B5B5B5;
  --line:#7FFFD4;
  --line-soft:#9FFFF0;
  --borde:#3D3D3D;
  --shadow:0 10px 20px rgba(0,0,0,.35);
}

*{ box-sizing:border-box }
body{
  background:var(--bg);
  color:var(--text);
  font-family:system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,'Helvetica Neue',Arial;
}

.timeline{
  max-width: 900px;
  margin: 2rem auto;
  padding: 1.25rem;
  text-align: left; /* alineado a la izquierda */
}
.timeline > h2{
  margin: 0 0 1rem 0;
  font-size: 1.6rem;
  letter-spacing: .3px;
  text-align: left;
}

/* === LÍNEA VERTICAL CON PULSO PERMANENTE === */
.timeline-list{
  position: relative;
  list-style: none;
  margin: 0;
  padding-left: 1.5rem;
}
.timeline-list::before{
  content:"";
  position:absolute;
  left:.55rem;
  top:0;
  bottom:0;
  width:3px;
  background: linear-gradient(var(--line), var(--line) 95%, transparent);
  animation: linePulse 4s ease-in-out infinite;
  transition: background .4s ease, box-shadow .3s ease;
}

/* ✨ Pulso permanente */
@keyframes linePulse {
  0%, 100% {
    box-shadow:
      0 0 10px rgba(127,255,212,.16),
      0 0 18px rgba(127,255,212,.10),
      inset 0 0 4px rgba(127,255,212,.16);
  }
  50% {
    box-shadow:
      0 0 14px rgba(127,255,212,.24),
      0 0 24px rgba(127,255,212,.16),
      inset 0 0 6px rgba(127,255,212,.22);
  }
}

/* ✨ Resplandor descendente en hover */
@keyframes lineGlow {
  0% {
    background: linear-gradient(var(--line-soft), transparent 10%);
    box-shadow: 0 0 12px rgba(127,255,212,.7);
  }
  100% {
    background: linear-gradient(var(--line-soft), transparent 100%);
    box-shadow: 0 0 0 rgba(127,255,212,0);
  }
}

/* Animación de aparición */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(14px); }
  to   { opacity: 1; transform: translateY(0); }
}

.timeline-item{
  position: relative;
  display: grid;
  grid-template-columns: 12ch 1fr;
  gap: .75rem 1rem;
  padding: .75rem 0 1.5rem;
  opacity: 0;
  animation: fadeUp .6s ease forwards;
  animation-delay: calc(var(--i) * 100ms);
}

/* === Puntos === */
.timeline-item .dot{
  position: absolute;
  left: -.15rem;
  top: .9rem;
  width: .9rem; height: .9rem;
  border-radius: 50%;
  background: var(--line);
  box-shadow: 0 0 0 .25rem rgba(127,255,212,.18);
  transition: background-color .3s ease, box-shadow .3s ease, transform .3s ease;
}

/* === Fecha === */
.timeline-item .date{
  font-weight: 600;
  color: var(--muted);
  padding-top: .3rem;
  padding-left: 1rem;
  transition: color .3s ease, text-shadow .3s ease;
}

/* === Tarjetas === */
.card {
  background: var(--card);
  border: 1px solid var(--borde);
  border-radius: 16px;
  padding: 1rem 1.25rem;
  box-shadow: var(--shadow);
  transition: transform .25s ease, box-shadow .25s ease, border-color .25s ease;
  cursor: default;
  text-align: left;
}

/* Hover sincronizado */
.timeline-item:hover .card {
  transform: translateY(-6px);
  border-color: var(--line);
  box-shadow:
    0 0 0 .25rem rgba(127,255,212,.12),
    0 12px 28px rgba(0,0,0,.45),
    0 0 22px rgba(159,255,240,.35);
}

/* Punto brillante */
.timeline-item:hover .dot {
  background: var(--line-soft);
  box-shadow: 0 0 12px rgba(127,255,212,0.7);
  transform: scale(1.2);
}

/* Fecha verde */
.timeline-item:hover .date{
  color: var(--line-soft);
  text-shadow: 0 0 8px rgba(127,255,212,.6);
}

/* Línea animada descendente */
.timeline-item:hover ~ .timeline-list::before,
.timeline-item:hover .timeline-list::before{
  animation: lineGlow 1s ease-out;
}

/* === Título === */
.title {
  margin: .1rem 0 .2rem;
  font-size: 1.05rem;
  color: var(--line);
  transition: color 0.3s ease, text-shadow 0.3s ease;
}
.timeline-item:hover .title {
  color: var(--line-soft);
  text-shadow: 0 0 8px rgba(127,255,212,0.6);
}

.inst{ margin: 0 0 .4rem; color: var(--muted); font-size: .95rem; }
.desc{ margin: .25rem 0 .6rem; line-height: 1.5; }

/* === Chips siempre verdes === */
.chips{
  display: flex; flex-wrap: wrap; gap: .4rem;
  list-style: none; padding: 0; margin: 0;
}
.chips li{
  padding: .2rem .55rem;
  border: 1px solid var(--line);
  border-radius: 999px;
  font-size: .8rem;
  color: var(--line);
  transition: transform .2s ease;
}
.chips li:hover{ transform: scale(1.05); }

/* Badge 'En curso' */
.badge{
  display: inline-block;
  margin-top: .6rem;
  padding: .25rem .55rem;
  border-radius: 8px;
  background: rgba(127,255,212,.10);
  border: 1px solid var(--line);
  font-size: .8rem;
}

/* === Encabezados sin subrayado === */
h1, h2 {
  color: var(--line);
  transition: color 0.3s ease, text-shadow 0.3s ease;
  margin-bottom: 1rem;
  text-align: left;
}
h1:hover, h2:hover {
  color: var(--line-soft);
  text-shadow: 0 0 8px rgba(127,255,212,0.6);
}

/* Accesibilidad: reducir animaciones si el usuario lo pide */
@media (prefers-reduced-motion: reduce){
  .timeline-list::before{ animation: none; }
}

@media (max-width: 600px){
  .timeline-item{ grid-template-columns: 1fr; }
  .timeline-item .date{ order: -1; }
}
</style>
