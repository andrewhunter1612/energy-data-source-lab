<template>
    <div>
        <google-chart type="BarChart" :data="mix" />
        <google-chart id="pie-chart" type="PieChart" :data="mix" />
        <google-chart type="ColumnChart" :data="mix" />
    </div>
</template>

<script>
import {GChart} from 'vue-google-charts'
    export default {
        name: 'display-info',
        props: ['mix'],
        data() {
            return {
                chartOptions: {
                    chart: {
                        fuel: 'Fuel',
                        perc: 'Percentage',
                    }
                }
            }
        },

        components:{
            'google-chart': GChart
        }
        
    }
</script>

<style lang="css" scoped>
#pie-chart{
    height: 800px;
    width: 800px;
    margin: 0px;
}
</style>