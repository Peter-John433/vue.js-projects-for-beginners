<template>
    <div  class="container">
       hello world this is compone component 
       <div>
          {{ items }}
       </div>
       <div>
          <input type="text" v-model="text">
       </div>

       <button @click="addBtn()">add</button>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                items:['car', 'house', 'tree'],
                text: ''
            }
        },

        methods:{
            addBtn(){
                this.items.push(this.text);
                this.text = ''
            }
        }
    }
</script>

<style scoped>
 .container{
    background-color: lightgreen;
    padding: 10px;
    width: 300px;
    margin: auto;
    height: 150px;
 }

 input{
    width: 100%;
    padding: 3px;

 }

</style>