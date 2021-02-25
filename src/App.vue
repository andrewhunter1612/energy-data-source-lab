<template>
  <div>
    <user-inputs />
    <display-charts :mix="energyData"/>
  

  </div>
</template>

<script>
import DisplayVue from './components/Display.vue'
import UserInputsVue from './components/UserInputs.vue'
  export default {

    data(){
      return {
        energyData: [['biomass', 'perc']]
      }
    },

    mounted(){
      fetch("https://api.carbonintensity.org.uk/generation")
      .then(res => res.json())
      .then(energyData => {
        let item = []
        for (let i = 0; i<energyData.data.generationmix.length; i++){
          const fuel = energyData.data.generationmix[i].fuel
          const perc = energyData.data.generationmix[i].perc
          item = [fuel, perc]
          this.energyData.push(item)
        }
      })
      
    },

    components:{
      'user-inputs': UserInputsVue,
      'display-charts': DisplayVue
    }
    
  }
</script>

<style lang="css" scoped>

</style>