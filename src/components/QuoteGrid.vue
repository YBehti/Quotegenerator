<template>
    <div class="row">
        <quote v-for="(quote,i) in quotes" @click.native="deleteQuote(i)">
            {{quote}}
        </quote>
    </div>
</template>

<script>
    import Quote from './Quote.vue'
    import {quoteBus} from "../main";

    export default {
        name: "QuoteGrid",
        props:['quotes'],
        components:{
            Quote
        },
        data(){
            return{
                quoteDeleted:[]
            }
        },
        methods:{
            deleteQuote(index){
                quoteBus.$emit('deletedQuote',index)

            }
        }
    }
</script>

<style scoped>

</style>