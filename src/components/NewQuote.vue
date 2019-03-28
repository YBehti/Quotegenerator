<template>
    <div class="row">
        <form action="">
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <label for="quote">Quote</label>
                <textarea class="form-control" name="quote" id="quote" cols="30" rows="3" v-model="quote"></textarea>
            </div>
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <button class="btn btn-primary" @click.prevent="createNew">Add Quote</button>
            </div>
        </form>

    </div>
</template>

<script>

    import {quoteBus} from "../main";

    export default {
        name: "NewQuote",
        data(){
            return{
                quote:null
            }
        },
        methods:{
            createNew(){

               quoteBus.$emit('newQuote',this.quote);
               this.quote = null

            }
        }

    }
</script>

<style scoped>

</style>