<template>
    <div class='button'>
        <button class='btn' 
        v-on:click='newJoke'>
        Click to get a joke!
        </button>
    </div>
</template>
<script>
export default {
   name: 'Button',
   
   methods: {
       newJoke:function(){
           this.$emit('newJoke');
     }
   }
};
</script>
<style scoped="">

.button {
    display: flex;
    justify-content: center;
    height: 150px;
    align-items: center;
    color:#f0f3bd;
    
}

.btn {
    color: white;
    border-radius: 20px;
    text-shadow: 0 1px 1px rgba(0, 0, 0, 0.2);
    background: #028090;
    font: fantasy;
    font-size: 125%
}

    
</style>