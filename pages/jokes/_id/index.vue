<template>
  <div>
      <nuxt-link to="/jokes">Back</nuxt-link>
      <h2>{{ joke }}</h2>
  </div>
</template>

<script>
    import axios from 'axios';
    export default {
        data(){
            return {
                joke:'loading...'
            }
        },
        head(){
            return {
                title:this.joke
            }
        },
        async created(){
            const config = {
                headers:{
                    Accept:'Application/json'
                }
            }

            try{
                const response = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`,config);
                this.joke=response.data.joke;
            }catch(err){
                console.log(err);
            }
        }
    }
</script>

<style>

</style>