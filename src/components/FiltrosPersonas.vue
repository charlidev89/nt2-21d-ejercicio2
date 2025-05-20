<template>
    <div class="mb-3">
        <div class="row">
            <div class="col-md-6">
                <label for="nombreFilter" class="form-label"><b>Filtrar por Nombre:</b></label>
                <input type="text" class="form-control" id="nombreFilter" placeholder="Buscar por nombre o apellido..."
                    v-model="nombreFilterLocal">
            </div>
            <div class="col-md-6">
                <label for="dniFilter" class="form-label"> <b>Filtrar por DNI</b>:</label>
                <input type="text" class="form-control" id="dniFilter" placeholder="Buscar por DNI..."
                    v-model="dniFilterLocal">
            </div>
        </div>
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
    emits: ['update:nombreFilter', 'update:dniFilter'],
    computed: {
        nombreFilterLocal: {
            get() {
                return this.nombreFilter
            },
            set(value) {
                this.$emit('update:nombreFilter', value)
            }
        },
        dniFilterLocal: {
            get() {
                return this.dniFilter
            },
            set(value) {
                this.$emit('update:dniFilter', value)
            }
        }
    }
}
</script>

