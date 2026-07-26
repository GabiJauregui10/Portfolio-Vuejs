<script setup>
import { ref } from 'vue'

// Datos personales
const nombre = 'Gabriel Jauregui'
const titulo = 'Técnico Universitario en Programación – UTN'
const telefono = '+54 2622308818'
const ubicacion = 'Tupungato, Mendoza, Argentina'

// CV descargable
const cvUrl = '/cv.pdf'

// Importación de íconos desde la carpeta local
import iconLinkedin from '@/components/icons/linkedin.svg'
import iconInstagram from '@/components/icons/instagram.svg'
import iconGithub from '@/components/icons/github.svg'

// Redes sociales
const redes = ref([
  { nombre: 'LinkedIn',  url: 'https://www.linkedin.com/in/gabriel-jauregui10/', icono: iconLinkedin },
  { nombre: 'Instagram', url: 'https://www.instagram.com/gabijauregui10/',       icono: iconInstagram },
  { nombre: 'GitHub',    url: 'https://github.com/GabiJauregui10',               icono: iconGithub },
])
</script>

<template>
  <section id="inicio" class="hero-wrapper">
    <div class="hero-card">
      <!-- Título principal -->
      <h1>{{ nombre }}</h1>
      <h3>{{ titulo }}</h3>

      <!-- Descripción -->
      <p class="intro">
        Hola, bienvenido a mi portafolio de proyectos. Soy un desarrollador web con experiencia
        en el desarrollo de aplicaciones web y móviles.
      </p>

      <!-- Redes sociales -->
      <div class="social">
        <a
          v-for="(red, index) in redes"
          :key="index"
          :href="red.url"
          target="_blank"
          rel="noopener noreferrer"
          :aria-label="red.nombre"
        >
          <img :src="red.icono" :alt="red.nombre" />
        </a>
      </div>

      <!-- Botón CV -->
      <a class="btn-primary" :href="cvUrl" download>
        <span>📄</span> Descargar CV
      </a>

      <!-- Datos personales -->
      <ul class="datos">
        <li>📞 Teléfono personal: {{ telefono }}</li>
        <li>📍 {{ ubicacion }}</li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
/* ===== INICIO / HERO (mejorado) ===== */

/* Mapea tus variables locales a la paleta global (con fallback) */
:root{
  --brand: var(--line, #7FFFD4);
  --brand-2: var(--line-soft, #9FFFF0);
  --hero-text: var(--text, #EDEDED);
  --hero-muted: var(--muted, #B5B5B5);
}

/* ==== Contenedor principal ==== */
.hero-wrapper{
  position: relative;
  padding: clamp(32px, 6vw, 72px) clamp(20px, 5vw, 60px);
  color: var(--hero-text);
  overflow: hidden;
}

/* Glow de fondo elegante (mantiene tu fondo general) */
.hero-wrapper::before{
  content:"";
  position:absolute; inset:-20%;
  background:
    radial-gradient(520px 520px at 14% 24%, color-mix(in oklab, var(--brand) 22%, transparent), transparent 60%),
    radial-gradient(420px 420px at 80% 85%, color-mix(in oklab, var(--brand-2) 16%, transparent), transparent 70%);
  filter: blur(18px);
  pointer-events:none;
  z-index:0;
}

/* === Tarjeta: seguimos sin fondo sólido, pero con sutil borde y blur === */
.hero-card{
  position: relative;
  padding: clamp(16px, 3vw, 28px);
  background: color-mix(in oklab, #161616 70%, transparent);
  border: 1px solid color-mix(in oklab, var(--brand) 18%, transparent);
  border-radius: 16px;
  box-shadow: 0 10px 20px rgba(0,0,0,.35);
  backdrop-filter: blur(8px);
  z-index: 1;
  transition: border-color .3s ease, box-shadow .3s ease, transform .25s ease;
}
.hero-card:hover{
  border-color: color-mix(in oklab, var(--brand-2) 60%, transparent);
  box-shadow:
    0 0 0 .25rem color-mix(in oklab, var(--brand) 18%, transparent),
    0 14px 32px rgba(0,0,0,.5);
  transform: translateY(-3px);
}

/* ==== Tipografía y jerarquía ==== */
h1{
  color: var(--brand);
  font-size: clamp(2.2rem, 5vw, 3.4rem);
  line-height: 1.05;
  margin: 0 0 .4rem 0;
  font-weight: 800;
  letter-spacing: .3px;
  text-shadow: 0 0 12px color-mix(in oklab, var(--brand) 28%, transparent);
}
h3{
  color: var(--brand-2);
  margin: 0 0 1rem 0;
  font-weight: 700;
  font-size: clamp(1.05rem, 1.6vw, 1.25rem);
}
.intro{
  color: var(--hero-muted);
  max-width: 58ch;
  line-height: 1.65;
  margin: 0 0 1.25rem 0;
}

/* ==== Redes sociales (círculos con glow sutil) ==== */
.social{
  display:flex; align-items:center; gap: 14px;
  margin: 10px 0 16px;
}
.social a{
  width: 46px; height: 46px; display:grid; place-items:center;
  border-radius: 50%;
  background: rgba(22,22,22,.65);
  border: 1px solid color-mix(in oklab, var(--brand) 18%, transparent);
  transition: transform .2s, box-shadow .3s, border-color .3s, background .3s;
}
.social a:hover{
  transform: translateY(-2px);
  border-color: var(--brand-2);
  background: rgba(22,22,22,.9);
  box-shadow: 0 0 0 6px color-mix(in oklab, var(--brand) 16%, transparent);
}
.social img{ width:22px; height:22px; filter: brightness(0) invert(1); }

/* ==== Botón CV (gradiente consistente con tu verde agua) ==== */
.btn-primary{
  display:inline-flex; align-items:center; gap:10px;
  background: linear-gradient(90deg, var(--brand-2), var(--brand));
  color:#0b1512;
  padding: 12px 18px;
  border-radius: 12px;
  text-decoration:none;
  font-weight: 800;
  letter-spacing: .2px;
  transition: transform .15s ease, box-shadow .3s ease, filter .2s ease;
  box-shadow: 0 10px 22px color-mix(in oklab, var(--brand) 22%, transparent), 0 0 0 1px #0c1a15 inset;
}
.btn-primary:hover{
  transform: translateY(-2px);
  box-shadow: 0 14px 28px color-mix(in oklab, var(--brand) 30%, transparent);
  filter: saturate(1.05);
}

/* ==== Datos personales ==== */
.datos{
  list-style:none; padding:0; margin: 10px 0 0;
  display:grid; gap:8px; color: var(--hero-text); opacity:.95;
}
.datos li{ display:flex; align-items:center; gap:10px; }
.datos svg{ width:18px; height:18px; fill: var(--brand); flex: 0 0 auto; }
.datos a{ color: var(--hero-text); text-decoration: underline transparent; transition: text-decoration-color .2s; }
.datos a:hover{ text-decoration-color: var(--brand-2); }

/* ==== Responsive ==== */
@media (max-width: 768px){
  .hero-card{ padding: 18px; }
  .social{ gap:12px; }
}
/* ✅ Quitar el fondo/glow de atrás del hero */
.hero-wrapper,
.hero-wrapper::before,
.hero-wrapper::after{
  background: transparent !important;
  box-shadow: none !important;
  filter: none !important;
}

.hero-wrapper::before{
  content: none !important;   /* elimina el pseudo-elemento */
}


</style>





