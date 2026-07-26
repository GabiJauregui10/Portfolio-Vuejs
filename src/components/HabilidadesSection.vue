<script setup>
import { ref } from 'vue'
import img1 from '/src/components/icons/JavaScript.svg';
import img2 from '/src/components/icons/Python.svg';
import img3 from '/src/components/icons/html.svg';
import img4 from '/src/components/icons/css.svg';
import img5 from '/src/components/icons/Java.svg';
import img6 from '/src/components/icons/sql.svg';
import img7 from '/src/components/icons/React.svg';
import img8 from '/src/components/icons/vue.svg';
import img9 from '/src/components/icons/Node.svg';
import img10 from '/src/components/icons/Django.svg';
import img11 from '/src/components/icons/Bootstrap.svg';
import img12 from '/src/components/icons/Git.svg';
import img13 from '/src/components/icons/Docker.svg';
import img14 from '/src/components/icons/Jenkins.svg';
import img15 from '/src/components/icons/Figma.svg';
import img16 from '/src/components/icons/VisualStudioCode.svg';
import img17 from '/src/components/icons/MySQL.svg';
import img18 from '/src/components/icons/PostgreSQL.svg';
import img19 from '/src/components/icons/MongoDB.svg';
import img20 from '/src/assets/EEUU.png';
import img21 from '/src/components/icons/Argentina.svg';


/** Íconos en /public/icons/ y rutas absolutas '/icons/...svg' */
const categorias = ref([
    {
    id: 1,
    nombre: 'Lenguajes de Programación',
    habilidades: [
      { id: 1, nombre: 'JavaScript', nivel: 'Avanzado',   icono: img1 },
      { id: 2, nombre: 'Python',     nivel: 'Intermedio', icono: img2 },
      { id: 3, nombre: 'HTML',   nivel: 'Avanzado',   icono: img3 },
      { id: 4, nombre: 'CSS' , nivel: 'Avanzado' , icono: img4 },
      { id: 5, nombre: 'Java',       nivel: 'Intermedio', icono: img5 },
      { id: 6, nombre: 'SQL',        nivel: 'Intermedio', icono: img6 },
    ]
  },
  {
    id: 2,
    nombre: 'Frameworks y Librerías',
    habilidades: [
      { id: 1, nombre: 'React.js',  nivel: 'Avanzado',   icono: img7 },
      { id: 2, nombre: 'Vue.js',    nivel: 'Intermedio', icono: img8 },
      { id: 3, nombre: 'Node.js',   nivel: 'Avanzado',   icono: img9 },
      { id: 4, nombre: 'Django',    nivel: 'Intermedio', icono: img10 },
      { id: 5, nombre: 'Bootstrap', nivel: 'Avanzado',   icono: img11 },
    ]
  },
  {
    id: 3,
    nombre: 'Herramientas y Software',
    habilidades: [
      { id: 1, nombre: 'Git',     nivel: 'Avanzado',   icono: img12 },
      { id: 2, nombre: 'Docker',  nivel: 'Intermedio', icono: img13 },
      { id: 3, nombre: 'Jenkins', nivel: 'Intermedio', icono: img14 },
      { id: 4, nombre: 'Figma',   nivel: 'Intermedio', icono: img15 },
      { id: 5, nombre: 'VS Code', nivel: 'Avanzado',   icono: img16 },
    ]
  },
  {
    id: 4,
    nombre: 'Bases de Datos',
    habilidades: [
      { id: 1, nombre: 'MySQL',      nivel: 'Intermedio', icono: img17 },
      { id: 2, nombre: 'PostgreSQL', nivel: 'Intermedio', icono: img18 },
      { id: 3, nombre: 'MongoDB',    nivel: 'Avanzado',   icono: img19 },
    ]
  },
  {
    id: 5,
    nombre: 'Idiomas',
    habilidades: [
      { id: 1, nombre: 'Inglés',  nivel: 'Intermedio', icono: img20 },
      { id: 2, nombre: 'Español', nivel: 'Nativo',     icono: img21 },
    ]
  },
])

/** Nivel -> porcentaje para barra */
const levelPercent = (nivel) => {
  const n = (nivel || '').toLowerCase()
  if (n.includes('nativo')) return 100
  if (n.includes('avanz'))  return 90
  if (n.includes('inter'))  return 65
  return 40
}
</script>

<template>
  <section class="skills-contenedor">
    <div v-for="categoria in categorias" :key="categoria.id" class="skills-categoria">
      <h3 class="categoria-titulo">{{ categoria.nombre }}</h3>

      <ul class="skills">
        <li
          v-for="skill in categoria.habilidades"
          :key="categoria.id + '-' + skill.id"
          class="skill"
          tabindex="0"
          :data-level="skill.nivel"
        >
          <img :src="skill.icono" :alt="skill.nombre" />
          <div class="skill-info">
            <div class="linea">
              <strong class="nombre">{{ skill.nombre }}</strong>
              <small class="nivel">· {{ skill.nivel }}</small>
            </div>
            <div class="progress">
              <div class="progress-fill" :style="{ width: levelPercent(skill.nivel) + '%' }" />
            </div>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<style >
/* ===== ALT+F4 COLOR THEME ===== */
:root {
  --bg: #0b0f12;
  --panel: #0f171a;
  --text: #e6f7f2;
  --muted: #a8c7c2;

  /* 🎨 Verde esmeralda ALT+F4 */
  --brand: #00c896;
  --brand-2: #1dd4b2;

  --chip: #101b1b;
  --chip-hover: #132525;
  --chip-border: #1a3538;

  --ring: rgba(0,200,150,0.22);
  --shadow: 0 10px 28px rgba(0,200,150,0.08);
  --shadow-strong: 0 14px 36px rgba(0,200,150,0.15);
}

/* Contenedor */
.skills-contenedor {
  max-width: 1100px;
  margin: auto;
  padding: clamp(1.4rem, 2.5vw, 2.4rem);
  background: linear-gradient(180deg, var(--panel) 0%, var(--bg) 100%);
  border: 1px solid rgba(255, 255, 255, .05);
  border-radius: 16px;
  color: var(--text);
}

/* Títulos en verde esmeralda */
.skills-categoria .categoria-titulo {
  color: var(--brand) !important;
  text-shadow: 0 0 10px rgba(0, 200, 150, .15);
  font-weight: 900;
  letter-spacing: .3px;
  margin: 0 0 .9rem 0;
  padding-left: .9rem;
  position: relative;
}
.skills-categoria .categoria-titulo::before {
  content: "";
  position: absolute;
  left: 0; top: .18rem;
  width: 4px; height: 1.15em;
  border-radius: 2px;
  background: linear-gradient(180deg, var(--brand), var(--brand-2));
}

/* Grid */
.skills {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 14px;
  padding: 0;
  list-style: none;
}

/* Tarjetas */
.skill {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 14px;
  border-radius: 12px;
  background: var(--chip);
  border: 1px solid var(--chip-border);
  box-shadow: var(--shadow);
  transition: all .25s ease-in-out;
  outline: none;
}

/* Avanzado = borde verde constante */
.skill[data-level*="Avanzado"] {
  border-color: var(--brand) !important;
}

/* Hover con contorno y glow verde suave */
.skill:hover,
.skill:focus-visible {
  background: var(--chip-hover);
  transform: translateY(-2px);
  border-color: var(--brand);
  box-shadow:
    0 0 6px var(--brand),
    0 0 14px rgba(0, 200, 150, 0.25),
    var(--shadow-strong);
}

/* Iconos */
.skill img {
  width: 30px;
  height: 30px;
  object-fit: contain;
  filter: drop-shadow(0 1px 1px rgba(0,0,0,.25));
}

/* Texto */
.skill-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 6px;
}
.linea {
  display: flex;
  align-items: baseline;
  gap: .45rem;
}
.nombre { font-weight: 700; }
.nivel { color: var(--muted); }

/* Barra de progreso */
.progress {
  height: 6px;
  border-radius: 999px;
  overflow: hidden;
  background: #0d1a1a;
  border: 1px solid #173335;
}
.progress-fill {
  height: 100%;
  border-radius: 999px;
  background: linear-gradient(90deg, var(--brand) 0%, var(--brand-2) 100%);
  box-shadow: 0 0 12px rgba(0,200,150,.25) inset;
  transition: width .35s ease;
}

/* Responsive */
@media (max-width: 768px) {
  .skills-categoria .categoria-titulo { text-align: center; }
}
</style>
