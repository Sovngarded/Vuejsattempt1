<template>
  <div>
    <ul>

      <todoItems
      v-for="(todoOneItem,i) of todosArray" :key="todoOneItem.id"
      v-bind:todoItem="todoOneItem"
      v-bind:index="i"
      v-on:removeItemList= "removeItemList"
      />
    </ul>
  </div>
</template>

<script>
import TodoItems from '@/components/TodoItem1'
  export default {
  props:['todosArray'],
  components: {
    TodoItems
  },
    methods: {
      removeItemList(id){
        this.$emit('removeItemList',id)
      }
    }

  }
</script>

<style scoped>
ul {
  list-style: none;
  margin:0;
  padding: 0;
}

</style>