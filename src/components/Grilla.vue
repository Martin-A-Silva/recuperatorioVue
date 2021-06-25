<template>
  <div>
    <b-card>
      <b-table ref="table" striped hover :items="entidades" :fields="fields">
        <template #cell(promedioPrecio)="data">
          {{ calcularPromedio(data.index) }}
        </template>
        <template #cell(Detalle)="data">
          <b-button @click="getPaisXNombre(data.item.name)" variant="primary"
            >Ver Detalle</b-button
          >
        </template>
      </b-table>
    </b-card>
  </div>
</template>

<script>
export default {
  props: ["entidades"],
  data() {
    return {
      fields: [
        "name",
        "capital",
        "region",
        "population",
        "area",
        "Detalle"
      ],
    };
  },
  methods: {
    getPaisXNombre(nombre) {
      this.$router.push(`/detalle/${nombre}`);
    },
    calcularPromedio(id) {
      let promedio = 0;
      this.$props.entidades[id].preciosRelevados.forEach((element) => {
        promedio += element;
      });
      promedio = promedio / this.$props.entidades[id].preciosRelevados.length;
      return promedio;
    },
  },
};
</script>

<style>
</style>