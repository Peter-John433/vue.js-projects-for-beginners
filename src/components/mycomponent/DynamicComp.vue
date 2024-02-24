<template>
    <div class="container">
       this project give us clear understanding on how to use vue dynamic component in our project
       <div>
            <button 
               type="button"
               @click="toggleComp = !toggleComp"
               >
              switch comp
            </button>
       </div>
       <keep-alive include="CompOne">
          <component :is="activeComp"></component>
       </keep-alive>

    </div>
</template>

<script>
//   import CompOne from './components/mycomponent/CompOne.vue';
// import CompOne from './components/mycomponent/CompOne.vue';
  import CompOne from './CompOne.vue';
  import CompTwo from './CompTwo.vue'
    export default {
        components:{ CompOne, CompTwo },
        name:'CompOne',
        data(){
            return{
                toggleComp: true
            }
        },

        computed:{
            activeComp(){
                if(this.toggleComp){
                    return CompOne
                }else{
                    return CompTwo
                }
            }
        }
        
    }
</script>

<style scoped>
  .container{
     margin-top: 2rem;
     display: flex;
     flex-direction: column;
     gap: 10px;
  }
</style>