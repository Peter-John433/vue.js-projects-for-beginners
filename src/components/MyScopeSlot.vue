<template>
    <div>
        <slot v-bind:text="data"></slot>
    </div>
    <div class="slot-array">
        <slot 
         v-for="item in foods"
         :key="item"
         :item="item"
        ></slot>
    </div>

    <div class="object-slot">
        <slot 
         v-for=" foodList in foodStuffs"
         :key="foodList.id"
         :foodName="foodList.name"
         :foodDes="foodList.des"
        >
        </slot>
    </div>

    <div>
        <slot
        dynamicText="hello dynamic"
        :jumpText="myWorld"
        >
        </slot>
    </div>

    <div>
        <slot name="rightSide"
        :giveText="gaveText"
        ></slot>
    </div>
    <div>
        <slot
        name="bottomSide" 
        :giveMe="pray"
        >

        </slot>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                data: 'my scope text from child comp to parent comp',

                foods:['apple', 'bannana', 'orange', 'grape'],

                foodStuffs:[
                    {
                        name: 'rice',
                        des: 'i love rice',
                        id: 1
                    },
                    {
                        name: 'beans',
                        des: 'i love beans',
                        id: 2
                    },
                    {
                        name: 'pizza',
                        des: 'i love pizza',
                        id: 3
                    }
                ],
                myWorld: 'create in me',
                gaveText: 'using name slot in scoped slot',
                pray: 'give it to her'
            }
        }
        
    }
</script>

<style scoped>
  /* .slot-array{
     background-color: green;
     display: flex;
     flex-direction: column;
     gap: 10px;
  } */

  .object-slot{
    display: flex;
    flex-direction: row;
    gap: 15px;
    justify-content: center;
    align-items: center;
    padding: 10px;
  }
</style>