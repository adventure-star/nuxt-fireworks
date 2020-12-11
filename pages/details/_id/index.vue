<template>
    <DetailBox :DBox="DBox" />
</template>

<script>
import DetailBox from '../../../components/DetailBox';
import axios from "axios";
export default {
    components : {
        DetailBox
    },
    data(){
        return{
            DBox:{}
        }
    },
    async created(){
        const config = {
            headers : {
                'Accept' : 'application/json',
            }
        }
        try{
            const res = await axios.get('https://fwemoviedb.herokuapp.com/3/movie/'+this.$route.params.id+'?api_key=e800e93ef4806616964242bbd2619ae1',config);
            this.DBox = res.data;
            //console.log(res.data)
        }catch(e){
            console.log(e)
        }
    },
    /* Header meta */
    head(){
        return {
            title : this.DBox.title,
            meta:[
                {
                    hid:"description",
                    name:"description",
                    content:"Fireworks Entertainment Latest Movies Here",
                }
            ]
        }
    },
}
</script>
