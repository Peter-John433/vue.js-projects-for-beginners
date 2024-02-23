<template>
  
  <div>
    <div class="text-1">
        This project give you more understanding on how to use props and emits in your vue project in the future.
    </div>
      <div class="food-items">
        <FoodItems
           v-for="item in foodItems"
           :item="item"
           :key="item"
           :item-name="item.name"
           :item-des="item.description"
           :item-fav="item.isFav"
           @toggle-favorite="recieveEmit"
        />
      </div>
  </div>
  <!-- fallthrough attribute project -->
  <div> 
    <div class="text-1">
        this project give us clear understnading on how to use the fallthrough attribute,fallthrough is an attribute that is pass to the component without it been declare in the recieving component
    </div>
    <div class="text-1">
       below is to-do project that desmonstrate fallthrough attribute
    </div>
    <div class="add">
     <input type="text" v-model="newItem" name="" id="">
     <button 
        type="button"
        @click="addItem()"
        >
        Add Item
      </button>
    </div>
    <div class="text-2">
        <ul>
          <Fall
            v-for="list in listOfCars" 
            :list="list"
            :key="list"
          />
        </ul>
    </div>
  </div>
  <!-- closed -->
  <!-- vue slot -->
    <div>
      <div class="text-1">
         this project give you clear understanding how to use vue slot in your project.
        <br>vue slot  allow us to reuse component with different structure, so we can customize the content of our components. vue slot is use to send content from parent component to the child component,on like props thats been recieved in the child component, vue slot is used as a placeholder of the content sent from the parent component so that when the project is display on the webpage the slot is been replaced with the content sent. 
      </div>
      <div class="my-slot">
          <my-slot
            v-for="name in slotProperties"
            :key="name"
          >
             <div class="img-3">
                <img :src="name.url" alt="">
             </div>
            <div class="slot-text">
              <div>
                  {{ name.name }}
              </div>
              <div>
                  {{ name.des }}
              </div>
            </div>
          </my-slot>
      </div>
      <!-- having empty component in the parent component then using default text on the child component -->
      <div>
         <my-slot>
           
         </my-slot>
      </div>
      <!-- closed -->
      <!-- using same component on footer -->
      <footer>
        <my-slot>
            footer
        </my-slot>
      </footer>
    </div>
  <!-- closed -->
  
</template>

<script>
   import FoodItems from './components/FoodItems.vue';
   import Fall from './components/Fall.vue';
   import MySlot from './components/MySLot.vue'
  export default {
    components: { FoodItems, Fall, 'my-slot': MySlot },
    data() {
      return{
        // for foodItems
        foodItems:[
          { name: 'rice', description: 'rice is nutrious and healthy', id: 1, isFav: true }, 
          { name: 'pizza', description: 'i love pizza ', id: 2, isFav: false },
          { name: 'beans', description: 'beans is nutrious and protenious in nature', id: 3, isFav: true },
          { name: 'yam', description: 'yam is also nutrious and healthy', id: 4, isFav: false }
        ],
        // closed

        // fallthrough
        listOfCars:['toyota', 'venza', 'modi', 'gle', 'glk'],
        newItem: '',
        //closed

        // slot properties
        slotProperties:[
           { url: 'src/assets/img/img-2.webp', name: 'robotic slot', id: 1, des: 'i love robotic slot1' },
           { url: 'src/assets/img/img-4.webp', name: 'robotic slot2', id: 2, des: 'i love robotic slot2' },
           { url: 'src/assets/img/img-img-2.webp', name: 'robotic slot3', id: 3, des: 'i love robotic slot3' },
           { url: 'src/assets/img/images-1.jpeg', name: 'robotic slot4', id: 4, des: 'i love robotic slot4' }
        ]
      }

    },
     methods:{
       recieveEmit(id, a){
          const findFood = this.foodItems.find(food => food.name === id);
          if(findFood){
             alert('you click :' + '\n' + id + '\n' + a)
          }
          findFood.isFav = !findFood.isFav
       },

       addItem(){
           this.listOfCars.push(this.newItem);
           this.newItem = ''

       }
     }
  }
</script>

<style scoped>
  .food-items{
     display: flex;
     justify-content: center;
     flex-direction: row;
     flex-wrap: wrap;
     align-items: center;
     gap: 10px;
     margin-top: 2rem;
  }

  .text-1{
     background-color: goldenrod;
     margin: 1rem 0;
     padding: 10px;
  }

   .add{
      margin-top: 2rem;
   }

  ul{
    margin-top: 20px;
    padding-left: 1rem;
    padding: 10px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  /* slot */
    .my-slot{
       display: flex;
       flex-direction: row;
       flex-wrap: wrap;
       justify-content: center;
       align-items: center;
       gap: 10px;
    }
    .img-3 img{
      width: 150px;
    }

    .slot-text{
       padding: 10px;
    }

    footer{
      background-color: pink;
      border: none;
      margin-top: 3rem;
      text-align: center;
    }

    
  /* closed */
</style>
<!-- 
  in this tutorial we learn how to 

  1 use option api to store datas
  2. register of child component in parent component
  3. pass datas as props from parent component to child component
  4. recieving of props in child component
  5. recieve props child component as an array or object
  6. how to use recieved props in child component to display our datas from parent component
  7. using a v-for directive to loop through our array of objects declared in parent data() function
  8. using the v-for key attribute 
  9. creating of favourite button to toggle between our food items
  10. how to use $emit() in the child component to sned information to parent component
  11. how to recieve $emit in parent component
  12. how to pass itemName and desName to parent component by using $emit() in child component
 -->

 <!-- 
   props is the process of passing data from parent component to the child component
   it's like sending a message from one person to another
   so when you send data from parent to child with props you are basically saying 
   "Hey child i have some information for you" 

  while 

  $emit(): is the process of passing information from child component to the parent component
  it's like sending a reply back to the sender 
  so when you emit something from child to parent you are basically saying   
  "Hey Parent i have done something and here is the result"

  these are some of the difference between props and $emit()

  Props must be declared in the component, while emits are just recommended to be documented.
  -->