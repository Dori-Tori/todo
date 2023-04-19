<template>
  <div>
    <input type="text" v-model="newTodoItem" placeholder="입력하세요" v-on:keyup.enter="addTodo">
    <button v-on:click="addTodo">추 가</button>
  </div>
</template>

<script>


export default {
  data (){
    return {
      newTodoItem : ''
    }
  },
  methods:{
    addTodo(){
      if(this.newTodoItem != ""){     
        var val = this.newTodoItem && this.newTodoItem.trim();
        this.$emit('addTodo' , val);  //localStorage.setItem(val , val);
        this.clearInput();
      }
    },
    clearInput(){
      this.newTodoItem = '';
    }

  }
}

</script>

<style scoped>
input:focus{
  outline: none;
}
.inputBox{
  background:white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input{
  border-style: none;
  font-size:0.9em;  
}

.addContainer{  
  float: right;
  background: linear-gradient(to right,#6478FB,#8763FB);
  display:inline-block;
  border-radius: 0 5px 5px 0;
}

.addBtn{
  color: white;
  vertical-align: middle;
}

</style>
