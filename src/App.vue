<template>
  <div id="app">
    <h1> JOPA</h1>
    <AddListItemForm
        @add-New-List-Item="addNewListItem"
    />
    <hr>
    <TodoList
        v-bind:todosArray="todosArray"
        @removeItemList="removeItemList"
      />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddListItemForm from '@/components/AddListItem'


export default {
  name: 'App',
  data(){
    return {
      todosArray:[
        {id: 1, title: 'jopa', completed: false},
        {id: 2, title: 'jopa1', completed: false},
        {id: 3, title: 'jopa2', completed: false}
      ]
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos/')
        .then(response => response.json())
        .then(json => this.todosArray = json)
  },
  methods:{
    removeItemList(id){
      this.todosArray = this.todosArray.filter(t => t.id !==id)
    },
    addNewListItem(todoItem){
      this.todosArray.push(todoItem)
    }
  },
  components: {
    TodoList,AddListItemForm

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
