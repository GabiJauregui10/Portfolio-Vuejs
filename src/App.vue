<script setup>
import NavBar from './components/NavBar.vue';
import DatosPersonales from './components/DatosPersonales.vue';
import Educacion from './components/Educacion.vue';
import ExperienciaSection from './components/ExperienciaSection.vue';
import ProyectosSection from './components/ProyectosSection.vue';
import HabilidadesSection from './components/HabilidadesSection.vue';
import InteresesSection from './components/InteresesSection.vue';
import FondoLava from './components/FondoLava.vue';
</script>

<template>
      <header id="top">
            <!--Barra de Navegacion-->
            <NavBar />
            <!--Componentes Datos Personales-->
            <DatosPersonales />
        </header>
        <main>
          <section id="educacion"><h2>Educacion - Cursos</h2>
            <Educacion />
          </section>
          <section id="experiencia"><h2>Experiencia Laboral</h2>
            <ExperienciaSection />
          </section>
          <section id="proyectos"><h2>Proyectos</h2>
            <ProyectosSection />
          </section>
          <section id="habilidades"><h2>Habilidades</h2>
            <HabilidadesSection />
          </section>
          <section id="intereses"><h2>Intereses</h2>
            <InteresesSection />
          </section>
          <section id="FondoLava">
            <FondoLava />
          </section>
        </main>
        <footer>
          <a href="#top">Inicio</a>
          <p>2025 Gabriel Jauregui - Portafolio web</p>
        </footer>
</template>

<style scoped>
footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  font-size: 1.3rem;
}
</style>
