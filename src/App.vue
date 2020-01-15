<template>
  <div id="app" class="container mt-4">
    <div class="row">
      <div class="col-md-4">
        <Category v-on:selectedCategory="selectCategory" :newtodo="newtodo" />
      </div>
      <div class="col-md-8">
        <Deneme v-bind:selectedCategory="selectedCategory" v-on:newtodo="addtodo" />
      </div>
    </div>
  </div>
</template>

<script>
import Deneme from "./components/Deneme.vue";
import Category from "./components/Category";
export default {
  name: "app",
  components: {
    Deneme,
    Category
  },
  data(){
    return{
        selectedCategory:{},
        newtodo:''
    }
  },
  methods:{
    selectCategory(value){
        this.selectedCategory=value;
    },
    addtodo(value){
        this.newtodo=value
    }
  }
};
</script>

<style>
</style>
