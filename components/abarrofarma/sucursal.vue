<template>
  <v-col>
    <v-container>
      <v-card>
        <v-card-title>Sucursales</v-card-title>
        <v-row>
          <v-col>
            <v-select
              v-model="dep"
              class="pl-3"
              label="Departamento"
              :items="departamentos"
              @change="actMun"
            ></v-select>
          </v-col>
          <v-col>
            <v-select
              v-model="mun"
              class="pr-3"
              label="Municipio"
              :items="municipios[dep]"
              @change="emitChange"
            ></v-select>
          </v-col>
        </v-row>
      </v-card>
    </v-container>
  </v-col>
</template>

<script>
export default {
  name: 'Sucursal',
  data() {
    return {
      dep: 'San Marcos',
      mun: 'Malacatan',
      departamentos: ['San Marcos'],
      municipios: {
        'San Marcos': [
          'San Marcos',
          'San Rafael',
          'San Pablo',
          'Malacatan',
          'Catarina',
          'Tecun Uman'
        ],
        Huehuetenango: [
          'Huehuetenango',
          'Chiantla',
          'Paquix',
          'Malacatancito',
          'Aguacatan'
        ],
        Retalhuleu: [
          'Retalhuleu',
          'Las Pilas',
          'Zapotitlan',
          'Mazatenango',
          'Colomba'
        ],
        Quetzaltenango: [
          'Quetzaltenango',
          'Salcaja',
          'San Carlos Sija',
          'Olintepeque'
        ]
      }
    }
  },
  methods: {
    emitChange() {
      this.$emit('change', this.mun)
    },
    actMun() {
      this.mun = this.municipios[this.dep][0]
      this.emitChange()
    }
  }
}
</script>
