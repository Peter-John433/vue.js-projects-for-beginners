<template>
    <div>
         <li>{{ list }}</li>
    </div>
</template>

<script>
    export default {
        props:['list']
        
    }
</script>

<style scoped>
  div{
    color: red;
    font-weight: bold;
    font-family: Arial, Helvetica, sans-serif;
  }

  li{
    list-style-type: none;
    background-color: lightgray;
    padding: 5px;
    width: 100px;
    text-align: center;
  }
</style>