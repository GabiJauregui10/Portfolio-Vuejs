<template>
  <section id="experiencia">
    <h2>Trayectoria profesional</h2>

    <article class="card exp" v-for="exp in experiencias" :key="exp.id">
      <header class="exp-head">
        <h3>{{ exp.titulo }}</h3>
        <span class="periodo">{{ exp.periodo }}</span>
      </header>
      <p class="empresa">{{ exp.empresa }}</p>
      <p class="desc">{{ exp.descripcion }}</p>
      <ul class="logros">
        <li v-for="l in exp.logros" :key="l">▸ {{ l }}</li>
      </ul>
      <div class="tags">
        <span v-for="t in exp.tags" :key="t" class="tag">{{ t }}</span>
      </div>
    </article>
  </section>
</template>

<script setup>
const experiencias = [
  {
    id:1,
    titulo:'Desarrollador Full Stack',
    empresa:'ALT+F4 Labs · Remoto · Mendoza, Argentina',
    periodo:'Enero 2022 – Octubre 2025',
    descripcion:'Responsable del desarrollo completo de soluciones web escalables y seguras.',
    logros:[
      'Lideré un equipo de 5 desarrolladores en e-commerce (ventas +35%).',
      'Diseñé e implementé APIs REST con Node.js/Express (MongoDB y PostgreSQL).',
      'Optimicé tiempos de carga en +50% con lazy loading y caché en React.',
      'Autenticación JWT/OAuth2; reducción de accesos no autorizados (-20%).',
      'CI/CD con Jenkins y Docker (deploys -40%).',
    ],
    tags:['Node.js','React','MongoDB','Docker','Jenkins','GitHub Actions','Scrum']
  },
  {
    id:2,
    titulo:'Desarrollador Backend Junior',
    empresa:'AndesTech · Tupungato, Mendoza',
    periodo:'Abril 2020 – Diciembre 2021',
    descripcion:'Microservicios y APIs internas bajo metodologías ágiles.',
    logros:[
      'Servicios REST con Java y Spring Boot para inventario y ventas.',
      'Consultas SQL optimizadas (-30% en respuesta).',
      'Integración con APIs externas y documentación con OpenAPI/Postman.',
      'Revisiones de código y control de versiones con Git.',
    ],
    tags:['Java','Spring Boot','PostgreSQL','Git','Postman','REST API']
  },
]
</script>

<style >
:root {
  --verde-agua: #7FFFD4;
  --verde-suave: #9FFFF0;
}

section {
  padding: 1rem;
  animation: fadeIn 1s ease-in-out;
}

h2 {
  margin: 0 0 1.4rem 0;
  font-size: 1.6rem;
  color: var(--verde-agua);
  letter-spacing: 0.5px;
  text-shadow: 0 0 10px rgba(127, 255, 212, 0.35);
}

/* Tarjetas */
.exp {
  padding: 1.4rem 1.6rem;
  margin: 1.2rem 0;
  border-radius: 16px;
  background: #161616; /* igual que tus cards */
  border: 1px solid rgba(127, 255, 212, 0.2);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.35);
  transition: all 0.3s ease;
  backdrop-filter: blur(8px);
}

.exp:hover {
  border-color: var(--verde-suave);
  box-shadow:
    0 0 0 .25rem rgba(127, 255, 212, 0.12),
    0 12px 28px rgba(0, 0, 0, .45),
    0 0 22px rgba(159, 255, 240, .35);
  transform: translateY(-4px);
}

/* Cabecera */
.exp-head {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

/* === TITULOS === */
h3 {
  margin: 0.3rem 0;
  color: var(--verde-agua);
  font-size: 1.35rem;
  font-weight: 700;
  text-shadow: 0 0 10px rgba(127, 255, 212, 0.45);
}

.periodo {
  color: var(--verde-suave);
  font-weight: 500;
  font-size: 0.95rem;
  opacity: 0.9;
}

/* Empresa */
.empresa {
  opacity: 0.9;
  margin: 0.4rem 0 0.8rem;
  color: #EDEDED;
  font-weight: 500;
}

/* Descripción */
.desc {
  opacity: 0.95;
  color: #B5B5B5;
  line-height: 1.6;
  font-size: 0.96rem;
}

/* Logros */
.logros {
  margin: 0.8rem 0 1rem 1rem;
  opacity: 0.95;
  color: #D3F7E8;
  list-style: "▸ ";
}

.logros li {
  margin-bottom: 0.4rem;
  transition: transform 0.2s ease, color 0.2s ease;
}

.logros li:hover {
  transform: translateX(4px);
  color: var(--verde-agua);
}

/* === ETIQUETAS === */
.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: 0.4rem;
}

.tag {
  border: 1px solid var(--verde-agua);
  color: var(--verde-agua);
  background: rgba(127, 255, 212, 0.08);
  padding: 0.3rem 0.8rem;
  border-radius: 999px;
  font-size: 0.88rem;
  font-weight: 500;
  transition: all 0.25s ease;
  box-shadow: 0 0 6px rgba(127, 255, 212, 0.1);
}

.tag:hover {
  background: var(--verde-agua);
  color: #161616;
  box-shadow: 0 0 14px rgba(127, 255, 212, 0.45);
  transform: translateY(-2px);
}

/* Animación de entrada */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}



</style>



