<template>
    <section>
        <h1>ENERGY WATCH</h1>
        <label for="chartType">Choose a data source: </label>
        <select v-on:change="handleSelect" v-model="selectedDataSource" id="chartType">
            <option value="1">Last 30 mins</option>
            <option value="2">Choose a time</option>
        </select>

        <date-time-picker v-if="selectedDataSource == 2" ></date-time-picker>
    </section>
</template>

<script>
import {eventBus} from '../main.js'
import DateTimePicker from './DateTimePicker.vue'
    export default {
        data() {
            return {
                selectedDataSource: null
            }
        },
        methods: {
            handleSelect(){
                eventBus.$emit('selected-data-source', this.selectedDataSource)
            }
        },
        components: {
            'date-time-picker': DateTimePicker
        }
        
    }
</script>

<style lang="css" scoped>
    h1{
        text-align: center;
        color: lime;
    }
</style>