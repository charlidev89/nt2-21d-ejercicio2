<template>
  <div 
    class="alert alert-warning" 
    v-if="debeMostrarAlerta"
    role="alert"
  >
    Por favor, ingrese al menos 3 caracteres en alguno de los filtros para realizar la búsqueda.
  </div>
</template>

<script>
export default {
  props: {
    nombreFilter: {
      type: String,
      default: ''
    },
    dniFilter: {
      type: String,
      default: ''
    }
  },
  computed: {
    debeMostrarAlerta() {
      // Mostrar alerta si alguno de los filtros está activo pero tiene menos de 3 caracteres
      return (this.nombreFilter.length > 0 && this.nombreFilter.length < 3) || 
             (this.dniFilter.length > 0 && this.dniFilter.length < 3)
    }
  }
}
</script>