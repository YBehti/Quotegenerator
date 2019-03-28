<template>
    <div class="container">
        <progress-bar :quotesCount="quotes.length" :maxQuote="maxQuote"></progress-bar>
        <new-quote></new-quote>
        <quote-grid :quotes="quotes"></quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on the quote to delete it!
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import {quoteBus} from "./main";
    import QuoteGrid from './components/QuoteGrid.vue'
    import NewQuote from './components/NewQuote.vue'
    import ProgressBar from './components/ProgressBar.vue'
    export default {
        components:{
            QuoteGrid,
            NewQuote,
            ProgressBar
        },
        data(){
            return{
                quotes:[
                    'just a quote'
                ],
                maxQuote:10
            }
        },
        created(){
            quoteBus.$on('newQuote',(quote)=>{
                if (this.quotes.length < this.maxQuote){

                    this.quotes.push(quote)
                }else{

                    alert('You have reached the limit, delete quote to add new one')
                }

            })
            quoteBus.$on('deletedQuote',(index)=>{
                this.quotes.splice(index,1)
            })
        }
    }
</script>

<style>
</style>
