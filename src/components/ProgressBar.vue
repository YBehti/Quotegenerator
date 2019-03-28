<template>
    <div class="row">
        <div class="col-sm-12">
            <h3>Quotes Limit</h3>
            <div class="progress">
                <div class="progress-bar"
                     role="progressbar"
                     aria-valuenow="60"
                     aria-valuemin="0"
                     aria-valuemax="100"
                     :style="{width:width+'%'}"
                >
                    {{quotesCount}}/{{maxQuote}}
                </div>
            </div>
        </div>
    </div>


</template>

<script>
    export default {
        name: "ProgressBar",
        props:['quotesCount','maxQuote'],


        computed:{
            width(){
               return (100/this.maxQuote)*this.quotesCount
            }
        }
    }
</script>

<style scoped>

</style>