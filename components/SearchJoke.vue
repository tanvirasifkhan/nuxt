<template>
  <form >
      <input type="text" @keyup="onSubmit" v-model="text" placeholder="Search jokes">
  </form>
</template>

<script>
export default {
    data(){
        return {
            text:''
        }
    },
    methods:{
        onSubmit(){
            this.$emit('search-text',this.text);
        }
    }
}
</script>

<style>
    input{
        border:1px solid #dedede;
        padding:10px 20px;
        border-radius: 5px;
        width:100%;
    }
</style>