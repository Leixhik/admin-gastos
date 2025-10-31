<script setup>
  import cerrarModal from '../assets/img/cerrar.svg'
</script>

<template>
  <div class="modal">
      <div class="cerrar-modal">
          <img
              :src="cerrarModal"
              alt=""
            />
      </div>
  </div>
</template>

<style scoped>
  .modal {
    position: absolute;
    background-color: rgb(0 0 0 / 0.9);
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
  }
</style>