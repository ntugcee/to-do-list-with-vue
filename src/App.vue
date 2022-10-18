<template>
<div class="container">
      <h1>To Do List</h1>
      <div>
        <input type="text" id="inputText" v-model="search"/>
        <input type="submit" id="addToDo" value="Add" />
        <input type="submit"  id="clearToDo" value="Remove" />
      </div>
      <div class="to-dos" id="toDoContainer"></div>
    </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup() {
    const search = ref ('')
    const searches = ref([])
    // boş bir arrayde tutma
    function addToDo() {
      searches.value.push({
        done: false,
        content: search.value,
      })
    }
    return {
      search,
      searches,
      addToDo,
    }
  },
}

</script>

<style>
body {
  margin: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  font-family: "Montserrat";
  background: linear-gradient(90deg, #c5e116, #ee7752, #e73c7e, #23a6d5);
  background-size: 500% 500%;
  animation: animaBG 10s ease infinite;
  /* linear infinite sonsuzluk  */
  animation-direction: alternate;
}
@keyframes animaBG {
  0% {
    background-position: 0%;
  }
  100% {
    background-position: 100%;
  }
}
.container h1 {
    width: 100%;
    text-align:center ;
    margin-top: 100px;
    color: #fff; ;
}
#inputText{
    width: 250px;
    height: 36px;
    border: 1px solid white;
    outline: none;
    border-radius: 15px;
    color:black;
}
#addToDo{
    height: 35px;
    width: 100px;
    border: 1px solid whitesmoke;
    vertical-align: center;
    font-size: 16px;
    cursor: pointer;
    outline: none;
    background-color:whitesmoke ;
    color: black;
    text-align: center;
    border-radius: 10px;
}
#addToDo:active{
    background: green;
}
#clearToDo:active{
    background: red;
}
#clearToDo{
    height: 35px;
    width: 100px;
    border: 1px solid whitesmoke;
    vertical-align: center;
    font-size: 16px;
    cursor: pointer;
    outline: none;
    background-color:whitesmoke ;
    color: black;
    text-align: center;
    border-radius: 10px;
}
#clearToDo{
  cursor: pointer;
}
.filtered {
  display: none !important;
}
</style>
