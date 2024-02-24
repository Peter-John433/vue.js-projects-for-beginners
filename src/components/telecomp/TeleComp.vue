<template>
     <button @click="this.activeComp = !this.activeComp">ActiveComp</button>
    <div class="container">
         <CompTele v-if="activeComp" />
    </div>
     
     {{ hello }}

     <div class="mable">
        <CompTwo />
     </div>

     <div>
        <Form />
     </div>
</template>

<script>
  import CompTele from './CompTele.vue';
  import CompTwo from './CompTwo.vue';
  import Form from './Form.vue';
    export default {
        components: { CompTele, CompTwo, Form },

        data(){
            return{
                activeComp: true,
                hello: '',

                nameOfPeople: [
                    {
                        name: 'john',
                        des: 'i love john',
                        id: 1
                    },
                    {
                        name: 'jenny',
                        des: 'i love jenny',
                        id: 2
                    },
                    {
                        name: 'martha',
                        des: 'i love martha',
                        id: 3
                    }
                ],

                dateEl: 'this is my date'
            }
        },
        
            provide() {
                return{
                    nameOfPeople : this.nameOfPeople,
                    dateEl : this.dateEl
                }
            }
       
        // // mounted(){
        // //     console.log('mounted')
        // // },
        // // unmounted(){
        // //     console.log('unmounted')
        // // },
        // // activated(){
        // //     console.log('activated')
        // // },
        // // deactivated(){
        //     // console.log('deactivated')
        // }
    }
</script>

<style scoped>
   .container{
     margin-top: 2rem;
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