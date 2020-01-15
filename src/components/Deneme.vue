<template>
  <div>
    <h1>{{ selectedCategory.title}}</h1>
    <hr />
    <p v-for="todo in selectedCategory.todos" v-bind:key="todo.id">{{ todo.text }}</p>
    <input type="text" class="form-control mt-3" 
    v-model="newtodo" placeholder="Add To Do.." 
    @keyup.enter="$emit('newtodo',newtodo); newtodo=''">
  </div>
</template>

<script>
export default {
  props: ["selectedCategory"],
  data(){
      return {
          newtodo:''
      }
  }
};
</script>

<style>
</style>