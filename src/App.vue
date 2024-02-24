<template>
  
  <div>
    <div class="text-1">
        <h1>props and $emit()</h1>
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
       <h1>fallthrough attri</h1>
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
        <h1>
          vue slot
        </h1>
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

  <!-- vue v-slot -->
    <div>
        <div class="text-1">
          <h1>v-slot and name slot</h1>
            this project give clear knowledge on how to use v-slot in your compenent, v-slot are use in the parent comp to direct your contents to the right path in your child component, for this to be successful you will have to name the slot in your child component and use the v-slot directive in your parent compenent.
        </div>

          <fall-slot>
             <template #sideSlot>
              <div>
                  using v-slot in my template
              </div>
             </template>
            <p>default slot</p>
          </fall-slot>
    </div>
  <!-- closed -->

  <!-- use of scope slot in parent comp -->
    <div>
       <div class="text-1">
        <h1>scope slot</h1>
       </div>
       <div class="scoped-slot">
           <my-scope-slot v-slot="myText">
              {{ myText.text }}
           </my-scope-slot>
       </div>
       <div class="slot-array">
         <my-scope-slot v-slot="food">
          <h2>{{ food.item }}</h2>
        </my-scope-slot>
       </div>
    </div>

    <div>
      <my-scope-slot v-slot="check">
        <div class="object-slot">
           <h3>{{ check.foodName }}</h3>
           <p>{{ check.foodDes }}</p>
        </div>
      </my-scope-slot>
    </div>

    <div>
       <my-scope-slot v-slot="writeText">
         <div>{{ writeText.dynamicText }}</div>
         <div>{{ writeText.jumpText }}</div>
       </my-scope-slot>
    </div>

    <div>
      <my-scope-slot v-slot:rightSide="rightText">
        <div>{{ rightText.giveText }}</div>
      </my-scope-slot>
    </div>
  <!-- closed -->
  
</template>

<script>
   import FoodItems from './components/FoodItems.vue';
   import Fall from './components/Fall.vue';
   import MySlot from './components/MySLot.vue';
   import FallSlot from './FallSlot.vue';
    import MySLot from './components/MySLot.vue';
    import MyScopeSlot from './components/MyScopeSlot.vue';
  export default {
    components: { 
            FoodItems, 
            Fall, 
            'my-slot': MySlot, 
            'fall-slot': FallSlot,
            'my-scope-slot': MyScopeSlot
          },
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

  .scoped-slot{
     background-color: pink;
     padding: 10px;
     font-size: 1rem;
     font-weight: bold;
     font-family: Arial, Helvetica, sans-serif;
  }

   .slot-array h2{
     color: white;
     display: flex;
     flex-direction: column;
     width: 120px;
     margin: 10px;
     background-color: green;
     text-align: center;
     padding: 10px;
     height: auto;
  }
  .object-slot{
    background-color: lightgray;
    margin: 10px;
    padding: 10px;
  }
</style>
<!-- 
   the root component ofr this project is app.vue while the child component is FoodItem.vue
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

  <!-- 
    THE PARENT COMPONENT FOR THIS PROJECT IS APP.VUE WHILE THE CHILD COMPONENT IS FALL.VUE
    
    In this project you will learn how to use the fallthrough attribute in your vue components,but firstly let explain what fallthrough means in vue js

    in a simple term fallthrough attribute are attribute that  will automatically passed down to any nested components, fallthrough are not directly delcare in the child component yet have access to the child component
    fallthrough are typically class,style and v-on  directives that can be used on any element
    they allow us to add classes, apply styles ,and bind events to elements dynamically 
    fall through attributes do not show up in the browser but will affect how the page looks

    1. fallthrough are merge with class or style attribute from child component

   -->

   <!-- 
    THE PARENT COMP FOR THIS PROJ IS APP.VUE WHILE THE CHILD COMP IS MYSLOT.VUE

    this project practice give you clear knowledge about vue slot but firstly we have to understand what vue slot means in the project

    VUE SLOT: is the process of passing content to the child component from the parent component, 
    vue slot act as the placeholder for the contents passed from the parent comp to child comp so that when the page is load on the website the vue slot will be replace by the content sent from the parent comp.
    
    quick way to use vue slot  is to use <slot> tag inside your child components template 
      -you don't need to define anything special in your child component 
      -the content passed into the <slot> tags goes where ever the <slot>  tag is placed in the child component 
      - duplicate the component name in your parent comp then add some content and it will be place again in the child compnent 
      - again add another slot name in parent comp without adding any content to it then go straight to your child comp and add content in youe vue slot and it will be replace on the webpage when the page is load. this process is called fallback in vue js
    -->

    <!-- 
      V-SLOT AND NAME-SLOT

      V-SLOT: is use for flexible and reusable  layouts, v-slot is use along with name-slot
      
      -name-slot is use in the child component to target a particular slot especially where slots are reused in a component
      -v-slot is use to direct the content passed from parent component to the named slot in the child component
      - nane is an attribute used in the slot tag in the child comp
      -v-slot is a directive that bind your name slot so the content passed csn be direct to the exact slot
      - if a slot tag is used in the child component without name attribute, the content passed from the parent will not be able to locate it but if the v-slot in the parent component is bind as default then the text will be replace in the child comp
      - comp name without v-slot directive send content directly to a slot tag in child comp without name tag
      - v-slot directive can also be use on template to send information to a particular name slot
      - v-slot as the shorthand # e.g #default
     -->