<template>
    <div class="container">
        this is my teleport container
       <teleport to='body'>
          hello world of teleport
       </teleport>
    </div>

    <div>
        <teleport to='#giveMe'>
            <div>bless giveMe again</div>
        </teleport>
    </div>

    <div id="giveMe">
        
    </div>
    <div>
        <div class="text-1">
                <h1>vue http request</h1>
            </div>
        <div>
            <div>HTTP REQUEST IN VUE</div>
        </div>
        

        <div class="data">
            <!-- <div>
                <button
                 @click="myData"
                >
                    fetch data
                </button>
           </div>

           <div v-if="data">
              <div>
                 {{ data.name }}
              </div>
              <div>
                   max-weight: {{ data.maxWeight }}
              </div>
           </div> -->

           <div>
              <button type="button" @click="fetchData">fetch data from api</button>
           </div>

           <div v-if="data">
               <div>
                   {{ data }}
               </div>
           </div>
        </div>

        <div>
            <h1>template refs</h1>

            <div ref="hello">
                grab my world of vue
            </div>

            <div ref="greed">

            </div>

            <button @click="addRef()">add refs</button>
        </div>

        <div class="before">
            {{ text }}
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                data: '',
                text: ''
            }
        },

        methods:{
        //    async myData(){
        //     const res = await fetch('./data/db.json');
        //     const deldata = await res.json();
        //     const numb = Math.floor(Math.random() * deldata.results.length);
        //     this.data = deldata.results[numb]
        //   }

         async fetchData(){
              const response = await fetch('https://random-data-api.com/api/v2/users');
              this.data = await response.json()
         },

         addRef(){
            this.$refs.greed.innerHTML = this.$refs.hello.innerHTML
         }
        },

        // created() {
        //     this.text = 'create me'
        //     console.log('hello world')
        // },

        
    }
</script>

<style scoped>
  .container{
     background-color: red;
     color: white;
     padding: 10px;
     width: 200px;
     text-align: center;
     margin: auto;
  }

  #giveMe{
    color: black;
    background-color: goldenrod;
    width: 150px;
    padding: 20px;
   }

   .text-1{
      background-color: goldenrod;
      margin: 2rem 0;
      padding: 10px;
   }

   .data{
      background-color: lightblue;
      width: auto;
      height: 400px;
   }

  .before{
     background-color: green;
     width: auto;
     height: 100px;
     color: white;
  }
</style>