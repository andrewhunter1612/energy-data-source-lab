<template>
    <section>
        <form action="">
            <h1>ENERGY WATCH</h1>
            <label for="chartType">Choose a data source: </label>
            <select v-on:change="handleSelect" v-model="selectedDataSource" id="chartType">
                <option value="1">Last 30 mins</option>
                <option value="2">Choose a time</option>
            </select>
            <section v-if="selectedDataSource == 2" >


            </section>
            
        </form>
        
    </section>
</template>

<script>
import {eventBus} from '../main.js'
import 
    export default {
        data() {
            return {
                selectedDataSource: null
            }
        },
        methods: {
            handleSelect(){
                eventBus.$emit('selected-data-source', this.selectedDataSource)
                console.log(this.selectedDataSource);
            }
        }
        
    }
</script>

<style lang="css" scoped>
    h1{
        text-align: center;
        color: lime;
    }
</style>