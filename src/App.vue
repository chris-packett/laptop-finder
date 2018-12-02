<template>
  <div id="app">
    <HelloWorld msg="Welcome to our Laptop Finder App!"/>
    <br>
    <input type="text" v-model="searchInput">
    <br>
    <br>
    <div class="laptop-table">
      <table class="table table-striped">
        <thead>
          <tr>
            <th scope="col">Laptop</th>
            <th scope="col">Rating</th>
            <th scope="col">Price</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="laptop in filteredLaptops" :key="laptop.id">
            <td>{{ laptop.name }}</td>
            <td>{{ laptop.rating }}</td>
            <td>${{ laptop.price }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data: function() {
    return {
      searchInput: '',
      laptops: [
        { id: 1, name: 'Thing 1', rating: '3.7', price: 100 },
        { id: 2, name: 'Thing 2', rating: '4.1', price: 80 },
        { id: 3, name: 'Thing 3', rating: '3.0', price: 180 }
      ]
    }
  },
  computed: {
    filteredLaptops() {
      return this.laptops.filter(laptop => {
        return (laptop.name.toLowerCase().includes(this.searchInput.toLowerCase()));
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.laptop-table {
  width: 75%;
  margin: auto;
}
</style>
