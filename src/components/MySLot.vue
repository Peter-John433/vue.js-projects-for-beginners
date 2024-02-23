<template>
    <div class="helo">
        <slot>
            this is my default slot
        </slot>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>
  .helo{
    color: green;
    border: 1px solid gray;
    /* width: 150px; */
    text-align: center;
  }
</style>