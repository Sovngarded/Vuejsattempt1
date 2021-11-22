<template>
  <li>
    <span v-bind:class="{listDone: todoItem.completed}">
      <input type="checkbox"  v-model="todoItem.completed">
      <strong>{{index+1}}</strong>
      {{todoItem.title}}
    </span>
    <button class="buttonRemoveItemList" v-on:click="$emit('removeItemList',todoItem.id)">&times;</button>
  </li>

</template>

<script>
export default {
  props:{
    todoItem:{
      type:Object,
      required:true
    },
index:Number
  }
}
</script>

<style scoped>
li{
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: .5rem 2rem;
  margin-bottom: 1rem;

}
.buttonRemoveItemList{
  background: red;
  color: #fff;
  border-radius: 50%;
  font-weight: bold;
}

input{
  margin-right: 1rem;
}

.listDone{
  text-decoration: line-through;
}

</style>