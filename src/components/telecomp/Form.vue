<template>
    <div>
       <form @submit.prevent="submitForm()">
        <div>
            <input type="radio" name="myFav" value="cat" v-model="animal" id="">
        </div>
        <div>
            <input type="radio" name="myFav" v-model="animal" value="pig">
        </div>
        <div>
            <input type="radio" name="myFav" value="dog" v-model="animal">
        </div>
        <div>
            <input type="radio" name="myFav" value="lion" v-model="animal" id="">
        </div>
        <button>submit</button>
      </form>
      <div class="animal">
           {{ myAnimal }}
      </div>

        <form @submit.prevent="submitForm">
            <div>
                <input type="checkbox" v-model="myBox" value="house">
                house
            </div>
            <div>
                <input type="checkbox" v-model="myBox" value="tree">
                tree
            </div>
            <div>
                <input type="checkbox" v-model="myBox" value="gold" >
                gold
            </div>
    
          <button>submit</button>
        </form>

      <div class="animal">
         {{  myAnimal2 }}
      </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                animal: '',
                myBox: [],
                myAnimal: 'nothing to display for now',
                myAnimal2: 'show checkboxs'
            }
        },
        methods:{
            submitForm(){
                if(this.animal){
                    this.myAnimal = this.animal;
                }

                if(this.myBox){
                    this.myAnimal2 = this.myBox
                }
            },

            // handleSubmit(){
            //     if(this.myBox){
            //         this.myAnimal2 = this.myBox
            //     }
            // }
        }
        
    }
</script>

<style scoped>
 .animal{
     background-color: red; 
     width: 200px;
     padding: 20px;
     color: white;
     margin: 1re auto;
 }

</style>