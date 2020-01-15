<template>
  <div>
    <ul class="list-group">
      <li class="list-group-item" style="cursor:pointer" v-for="category in categories" @click="selectCategory(category)" v-bind:class="{'active' : selectedCategory==category}" v-bind:key="category.id">{{ category.title }}</li>
    </ul>
    <input type="text" class="form-control mt-3" placeholder="Type category.." v-model="newCategory" @keyup.enter="addCategory" name id />
  </div>
</template>

<script>
export default {
  data() {
    return {
      categories: [
        {
          id: 1,
          title: "Genel",
          todos: []
        },
        {
          id: 2,
          title: "Bilgisayar",
          todos: []
        },
        {
          id: 3,
          title: "Spor",
          todos: []
        }
      ],
      newCategory: "",
      selectedCategory:{}
    };
  },
  methods: {
    addCategory() {
      if (this.newCategory != "") {
        this.categories.push({
          id: this.categories[this.categories.length - 1].id + 1,
          title: this.newCategory,
          todos: []
        });
        this.newCategory = "";
      }
    },
    selectCategory(category){
        this.selectedCategory=category;
        this.$emit('selectedCategory',this.selectedCategory);
        
    },
    getId(dizi=[]){
      if(dizi.length!=0){
        return (dizi[dizi.length-1].id)+1;
      }
      else{
        return 1;
      }
        
    }
  },
  created(){
      this.selectedCategory=this.categories[0];
      this.$emit('selectedCategory',this.selectedCategory);
  },
  watch:{
    newtodo(value){
        this.selectedCategory.todos.push({id:this.getId(this.selectCategory.todos),text:value,done:false})
    }
  },
  props:['newtodo']

};
</script>

<style>
</style>