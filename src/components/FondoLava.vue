<template>
  <div class="fondo-lava">
    <div class="blob"></div>
    <div class="blob2"></div>
  </div>
</template>

<style scoped>
.fondo-lava {
  position: fixed;
  inset: 0;
  overflow: hidden;
  background-color: #0b0f12;
  z-index: -1;
}
.blob, .blob2 {
  position: absolute;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle at 30% 30%, #00c896, #0b0f12 70%);
  border-radius: 40%;
  filter: blur(120px);
  opacity: 0.7;
  animation: movimiento 18s ease-in-out infinite alternate;
}
.blob2 {
  width: 600px;
  height: 600px;
  top: 40%;
  left: 50%;
  background: radial-gradient(circle at 70% 70%, #1dd4b2, #0b0f12 70%);
  animation-delay: 3s;
}

@keyframes movimiento {
  0% { transform: translate(-10%, -10%) scale(1); }
  50% { transform: translate(20%, 30%) scale(1.2); }
  100% { transform: translate(-15%, 15%) scale(1); }
}
</style>

