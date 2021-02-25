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

                // chartData: [
                //     ['Fuel', 'perc', 'perc'],
                //     ['biomass', 20, 30],
                //     ['biomass', 20, 30],
                //     ['biomass', 20, 30]
        // ['Year', 'Sales', 'Expenses', 'Profit'],
        // ['2014', 1000, 400, 200],
        // ['2015', 1170, 460, 250],
        // ['2016', 660, 1120, 300],
        // ['2017', 1030, 540, 350]
    //   ],
    //   chartOptions: {
    //     chart: {
    //       title: 'Company Performance',
    //       subtitle: 'Sales, Expenses',
    //     }
    //   }
                
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