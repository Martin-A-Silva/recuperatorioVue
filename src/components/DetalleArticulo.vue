<template>
  <div>
    <b-container fluid>
      <b-row><br /></b-row>
      <b-row>
        <b-col>
          <img :src="articulo.flag" height="100px" width="200px" />
          <b-row style="text-align: left">
            <br />
            Descripción: <br /><br />{{ articulo.articulo }}
          </b-row>
        </b-col>
        <b-col
          style="
            border-left-style: solid;
            border-left-width: 1px;
            border-left-color: lightgrey;
          "
        >
          <b-col style="text-align: left">
            <b-row>
              <b-col> Nombre </b-col>
              <b-col>{{ articulo.name }}</b-col>
            </b-row>
            <b-row>
              <b-col> Capital</b-col>
              <b-col> {{ articulo.capital }} </b-col>
            </b-row>
            <b-row>
              <b-col> Region </b-col>
              <b-col>
                {{ articulo.region }}
              </b-col>
            </b-row>
            <b-row>
              <b-col>Subregion</b-col>
              <b-col>{{ articulo.subregion }}</b-col>
            </b-row>
            <b-row>
              <b-col>Poblacion </b-col>
              <b-col>{{ articulo.population }}</b-col>
            </b-row>
            <b-row>
              <b-col>Superficie </b-col>
              <b-col>{{ articulo.area }} </b-col>
            </b-row>
            <b-row>
              <b-col>Fronteras </b-col>
              <b-col
                ><ul id="example-1">
                  <li v-for="item in articulo.borders" :key="item" >
                    {{ item }}
                  </li>
                </ul></b-col
              >
            </b-row>
          </b-col>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  name: "DetalleArticulo",
  props: ["articulo"],
  mounted() {},
  data() {
    return {
      productoEncontrado: [],
    };
  },
  methods: {},
};
</script>

<style>
</style>