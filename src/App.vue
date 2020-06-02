<template>
  <div id="app">
    <label >Choose a Category:</label>
    <select v-model="category">
      <option value="Book">Books</option>
      <option value="Magazine">Magazines</option>
      <option value="Newspaper">Newspapers</option>
      <option value="Others">Others</option>
      <option value="All">All</option>
    </select>
    <br>
    <input v-model="name" placeholder="Escriba el nombre" />
    <table id="table" border = "1" >
      <thead>
        <tr>
          <th>Code</th>
          <th>Name</th>
          <th>Description</th>
          <th>Category</th>
        </tr>
      </thead>
      <tbody>
        <tr :key="item.code" v-for="item in filteredList">
          <td>{{ item.code }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.description }}</td>
          <td>{{ item.category }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
//import data from "./data.json";
import * as data from "./data2.json";

export default {
  name: 'App',
  components: {
  },

  data(){
    return{
      category:"",
      name:"",
      //list: data
      list: data.obj
    }
    
  },

  computed: {
    filteredList() {
      const listByCategory = 
      this.category === "" || this.category === "All"
        ? this.list
        : this.list.filter(item => item.category === this.category);
      return this.name === ""
        ? listByCategory
        : listByCategory.filter(item => item.name === this.name);
    }
  },

  
}
</script>

<style>
table {
   width: 100%;
   border: 1px solid #000;
}
th, td {
   width: 25%;
   text-align: left;
   vertical-align: top;
   border: 1px solid #000;
}

</style>
