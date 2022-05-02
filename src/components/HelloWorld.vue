<template>
    <h1 class="hello text-light"> {{ this.result }} </h1>
    <table class="table table-dark table-striped">
      <thead>
      <tr>
        <th scope="col">id</th>
        <th scope="col">algol</th>
        <th scope="col">mas</th>
        <th scope="col">algomas</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="item in this.tabla" :key="item.id">
        <th scope="row"> {{ item.id }} </th>
        <td> {{ item.algol }} </td>
        <td> {{ item.mas }} </td>
        <td> {{ item.algomas }} </td>
      </tr>
      </tbody>
    </table>
</template>

<script>
// import what you need
import axios from 'axios';
export const envvars = {
  production: false,
  backendurl: 'http://localhost:8080'
};
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: () => ({
    result: null,
    tabla: null,
  }),
  created() {
    axios.get(`${ envvars.backendurl}/endpoint/hello`).then((result) => {
      this.result = result.data;
    });
    axios.get(`${ envvars.backendurl}/endpoint/getUrls`).then((tabla) => {
      this.tabla = tabla.data;
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
