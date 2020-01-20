<template>
  <div id="app">
 
    <todo />
    
    <router-view/>
  </div>
</template>

<script>
import Todo from './Components/Todo';

export default{
  name:'App',
  components:{
    Todo
  }
  
}
</script>

<style>


   #app{
  background-color: #E4E9FD;
  background-image: -webkit-linear-gradient(65deg, #A683E3 50%, #E4E9FD 50%);
  min-height: 1000px;
  font-family: 'helvetica neue';
}

</style>
