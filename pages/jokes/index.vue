<template>
    <div>
        <search-joke @search-text="searchText"></search-joke>
        <joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/>
    </div> 
</template>

<script>
    import axios from 'axios';
    import Joke from '../../components/Joke.vue';
    import SearchJoke from '../../components/SearchJoke.vue';
    export default {
        components:{
            Joke,
            SearchJoke
        },
        data(){
            return {
                jokes:[]
            }
        },
        head(){
            return {
                title:'Jokes'
            }
        },
        async created(){
            const config = {
                headers:{
                    Accept:'Application/json'
                }
            }

            try{
                const response = await axios.get('https://icanhazdadjoke.com/search',config);
                this.jokes=response.data.results;
            }catch(err){
                console.log(err);
            }
        },
        methods:{
            async searchText(text){
                const config = {
                    headers:{
                        Accept:'Application/json'
                    }
                }

                try{
                    const response = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`,config);
                    this.jokes=response.data.results;
                }catch(err){
                    console.log(err);
                }
            }
        }
    }
</script>

<style>

</style>