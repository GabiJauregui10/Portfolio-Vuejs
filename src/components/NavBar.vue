<template>
  <nav class="navbar">
    <ul>
      <li v-for="item in items" :key="item.href">
        <a class="nav-link" :href="item.href">{{ item.label }}</a>
      </li>
    </ul>
  </nav>
</template>

<script setup>
const items = [
  {label:'Educación', href:'#educacion'},
  {label:'Experiencia', href:'#experiencia'},
  {label:'Proyectos', href:'#proyectos'},
  {label:'Habilidades', href:'#habilidades'},
  {label:'Intereses', href:'#intereses'},
]
</script>

<style scoped>
.navbar{
  position:sticky; top:0; z-index:10;
  background: transparent;
  padding: .6rem .8rem;
  backdrop-filter: blur(4px);
}
ul{display:flex;gap:.6rem;list-style:none;margin:0;padding:0;justify-content:center}
.nav-link{
  display:inline-block; padding:.45rem .9rem; border-radius:10px;
  border:1px solid rgba(255,255,255,.08);
  color:#e6f7f2; text-decoration:none; transition:.25s;
}
.nav-link:hover, .nav-link:focus-visible{
  color:var(--brand); border-color:var(--brand);
  box-shadow:0 0 8px rgba(0,200,150,.25);
}
</style>


