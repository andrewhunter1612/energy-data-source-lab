<template>
  <div>
    <user-inputs />
    <display-charts v-if="energyData.length > 1" :mix="energyData"/>
  

  </div>
</template>

<script>
import DisplayVue from './components/Display.vue'
import UserInputsVue from './components/UserInputs.vue'
import { eventBus } from './main'
  export default {

    data(){
      return {
        energyData: [['biomass', 'perc']],
        dateDate: null,
        dataSource: null,
        startDate: null, 
        endDate: null
      }
    },

    mounted(){
      
      eventBus.$on('selected-data-source', selected => {
        if (selected==1){
          this.fetchData('https://api.carbonintensity.org.uk/generation')
        }
        // else if (selected==2) {
          // eventBus.$on('chosen-start-date', (selected) => {
          //   this.startDate = selected
          // })
          // eventBus.$on('chosen-end-date', selected => {
          //   this.endDate = selected
            let apiSource = 'https://api.carbonintensity.org.uk/generation/'+this.startDate+"T12:00Z/"+this.endDate+"T12:30Z"
          //   console.log(apiSource);
          //   fetch(apiSource)
          //     .then(res => res.json())
          //     .then(dateDate => {
          //       console.log('date', dateDate);
          //       for (let item of dateDate.data){
          //         console.log(item);
                  // for (let position of item){
                  //   console.log('postion', position.data);
                  // }
                  // console.log(item);
                // }

                // this.dateDate = [['fuel', 'perc'], ...dateDate.data.generationmix.map(({fuel, perc}) => ([fuel, perc]))]
                // console.log('energy', this.dateDate);
                // })
      //     }  
      // )
      //   }

    })},
    methods: {
      fetchData(url){
        fetch(url)
          .then(res => res.json())
          .then(energyData => {
            this.energyData = [['fuel', 'perc'], ...energyData.data.generationmix.map(({fuel, perc}) => ([fuel, perc]))]
            console.log('energy', this.energyData);
            // let item = []
            // for (let i = 0; i<energyData.data.generationmix.length; i++){
            //   const fuel = energyData.data.generationmix[i].fuel
            //   const perc = energyData.data.generationmix[i].perc
            //   item = [fuel, perc]
            //   this.energyData.push(item)
            // }
        })
      }
    }
    ,

    components:{
      'user-inputs': UserInputsVue,
      'display-charts': DisplayVue
    }
    
  }
</script>

<style lang="css" scoped>

</style>