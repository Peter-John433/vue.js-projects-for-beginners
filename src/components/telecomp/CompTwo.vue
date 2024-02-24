<template>
    <div class="container">
        <h1>Provide and Inject</h1>
        
        <div class="mable">
            <div v-for="x in nameOfPeople">
                <div>{{ x.name }}</div>
                <div>{{ x.des }}</div>
            </div>
        </div>
       <div>
          {{ dateEl }}
       </div>
    </div>
</template>

<script>
    export default {
        inject:['nameOfPeople', 'dateEl']
    }
</script>

<style scoped>
  .container{
     margin: 2rem auto;
     background-color: lightgreen;
     width: auto;
     height: 200px;
  }

  /* .mable{
    background-color: red;
    color: white;
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin: 10px;
  } */
</style>