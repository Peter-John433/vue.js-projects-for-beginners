<template>
    <div>
        <div class="div">
            <slot name="topSlot">
            
            </slot>
        </div>
        
        <div class="div">
            <slot>

            </slot>
        </div>

        <div class="div">
            <slot name="sideSlot">
            
            </slot>
        </div>
        
    </div>
</template>

<style scoped>
   .div{
     background-color: green;
     padding: 10px;
     margin: 10px auto;
     color: white;
     width: 200px;

   }
</style>