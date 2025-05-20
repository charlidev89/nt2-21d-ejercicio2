<template>
  <div class="container-fluid mt-3 ">
    <h1>Listado de Personas</h1>
    
    <!-- Filtros -->
    <FiltrosPersonas
      v-model:nombreFilter="nombreFilter"
      v-model:dniFilter="dniFilter"
    />
    
    <!-- Alerta -->
    <AlertaFiltro
      :nombreFilter="nombreFilter"
      :dniFilter="dniFilter"
    />
    
    <!-- Lista de personas -->
    <div class="card-deck m-0">
      <div class="row">
        <div 
          class=" col-md-6 mx-auto " 
          v-for="persona in personasFiltradas" 
          :key="persona.dni"
        >
          <PersonaCard :persona="persona" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FiltrosPersonas from './components/FiltrosPersonas.vue'
import AlertaFiltro from './components/AlertaFiltro.vue'
import PersonaCard from './components/PersonaCard.vue'

export default {
  components: {
    FiltrosPersonas,
    AlertaFiltro,
    PersonaCard
  },
  data() {
    return {
      nombreFilter: '',
      dniFilter: '',
      personas: [
        {
          nombre: "Daniel",
          apellido: "Sanchez",
          correo: "danielsanchez68@hotmail.com",
          dni: "20442873"
        },
        {
          nombre: "Juan",
          apellido: "Perez",
          correo: "j@p.gmail.com",
          dni: "12345678"
        },
        {
          nombre: "Ana",
          apellido: "Suarez",
          correo: "a@s.gmail.com",
          dni: "87654321"
        },
        {
          nombre: "Carlos",
          apellido: "Arteaga",
          correo: "dakaricarlos@gmail.com",
          dni: "35223332"
        }
      ]
    }
  },
  computed: {
    personasFiltradas() {
      // Si ambos filtros están vacíos, mostrar todo
      if (!this.nombreFilter && !this.dniFilter) {
        return this.personas;
      }
      
      let resultado = [...this.personas];
      
      //  filtro por nombre si tiene más de 2 caracteres
      if (this.nombreFilter && this.nombreFilter.length >= 3) {
        const busqueda = this.nombreFilter.toLowerCase();
        resultado = resultado.filter(persona => 
          `${persona.nombre} ${persona.apellido}`.toLowerCase().includes(busqueda)
        );
      }
      
      //  filtro por DNI si tiene más de 2 caracteres
      if (this.dniFilter && this.dniFilter.length >= 3) {
        resultado = resultado.filter(persona => 
          persona.dni.includes(this.dniFilter)
        );
      }
      
      return resultado;
    }
  }
}
</script>