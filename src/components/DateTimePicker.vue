<template>
    <div>
        <form v-on:submit.prevent="dateTimeSelect" id="date-time-form" action="">
            <label for="start-date">Enter start date: </label>
            <input type="date" v-model="chosenDate" id="start-date">

            <label for="end-date">Enter end date: </label>
            <input type="date" v-model="chosenEndDate" id="end-date">

            <!-- <label for="time">Enter time: </label>
            <input type="time" v-model="chosenTime" id="time"> -->

            <input type="submit" value="Enter">
        </form>
    </div>
</template>

<script>
import {eventBus} from '../main.js'
    export default {
        name: 'date-time-picker',
        data(){
            return {
                chosenDate: null,
                chosenTime: null,
                chosenEndDate: null
            }
        },
        methods: {
            dateTimeSelect(){
                eventBus.$emit('chosen-start-date', this.chosenDate)
                eventBus.$emit('chosen-end-date', this.chosenEndDate)
                // eventBus.$emit('chosen-end-date', this.chosenTime)
                // console.log('time', this.chosenEndDate, 'date', this.chosenDate);
            }
        }
        
    }
</script>

<style lang="css" scoped>

#date-time-form{
    display: flex;
    flex-wrap: wrap;
}

</style>