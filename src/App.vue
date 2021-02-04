<template>
  <div id="app">
       <table class="table">
            <thead>
                <th>Name</th>
                <th>Url</th>
            </thead>
            <tbody>
                <tr v-for="pokemon in pokemons" :key="pokemon.id">
                    <td>{{ pokemon.name }}</td>
                    <td>{{ pokemon.url }}</td>
                </tr>
            </tbody>
       </table>

  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
        pokemons:[]
    }
  },
  async created(){
        var response = await fetch('http://localhost:8000/api/pokemons/');
        this.pokemons = await response.json();
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
