<template>
   
  <div class="items-container">
     <div class="item-name">
       {{ itemName }}
     </div>
     <div class="item-des">
        {{ itemDes }}
     </div>
     <div 
       class="fav-btn"
       >
        <button
          @click="toggleFav()"
        >
          favorite
        </button>
     </div>
     <div class="fav-img">
        <img src="../assets/img/img_quality.svg" v-show="itemFav" alt="">
     </div>
  </div>
</template>

<script>
  export default {
    //  props: ['itemName', 'itemDes', 'itemFav'],
    props:{
      itemName:{
         type: String,
         require: true
      },
      itemDes:{
        type: String,
        require: true
      },
      itemFav:{
        type: Boolean,
        require: true
      }
    },
    emits:['toggle-favorite'],
    data(){
      return{
         
      }
    },

    methods:{
       toggleFav(){
          this.$emit('toggle-favorite', this.itemName, this.itemDes)
       }
    }

  }
</script>

<style scoped>
   .items-container{
     background-color: lightgray;
     display: flex;
     flex-direction: column;
     gap: 20px;
     justify-content: start;
     position: relative;
     padding: 10px;
     width: 200px;
     height: 150px;
     box-shadow: 1px 1px 2px lightgray;
     border-radius: 6px;
   }
   .fav-img img{
      max-width: 30px;
      width: 100%;
      object-fit: cover;
      position: absolute;
      top: 5%;
      right: 5%;

   }

   .item-name{
     font-weight: bold;
     text-transform: capitalize;
     font-size: 20px;
     font-family: Arial, Helvetica, sans-serif;
   }

   .item-des{
     text-transform: capitalize;
     font-size: 14px;
     font-family: Arial, Helvetica, sans-serif;
   }

   .fav-btn button{
     font-weight: bold;
     text-transform: capitalize;
     font-family: Arial, Helvetica, sans-serif;
     background-color: white;
     border: 1px solid gray;
     border-radius: 4px;
     cursor: pointer;
     padding: 3px 5px;
   }
</style>