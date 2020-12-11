<template>    
    <div class="container mx-auto pb-4">
        <SearchListBox v-for="lbox in results" :key="lbox.id" :SLBox="lbox" />
    </div>
</template>

<script>
import CardListBox from '../../../components/SearchListBox';
import axios from "axios";
export default {
    components:{
        SearchListBox,
    },
    data(){
        return {
            results:[],
        }
    },
    async created(){
        //console.log(this.$route.params.queryText)
        if(this.$route.params.queryText!==undefined){
            const config = {
                headers : {
                'Accept' : 'application/json',
                }
            }
            try{
                const res = await axios.get('https://fwemoviedb.herokuapp.com/3/search/movie?api_key=e800e93ef4806616964242bbd2619ae1&query='+this.$route.params.queryText,config);
                this.results = res.data.results   
                //console.log(res.data)
            }catch(e){
                console.log(e)
            }
        }else{
            console.log('inside')
        }
    },
    methods:{
        async onSearchFormSubmit(queryText){
            console.log('inside')
        }
    },
    /*index Header */
    head(){
        return {
            title : 'Movies on " '+ this.$route.params.queryText+' "',
            meta:[
                {
                    hid:"description",
                    name:"description",
                    content:"Fireworks Entertainment Latest Movies Here",
                }
            ]
        }
    }
}
</script>
