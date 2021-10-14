<template>
  <div class="id">

  </div>
</template>

<script>
import axios from 'axios';
// import moment from 'moment';
export default {
  name: 'App',
  components: {
    
  },
  data(){
    return{
    arrConfirmed:[],
    arrDeaths:[],
    arrDeathRate:[],
    arrPopulation:[],
    }
    
  },
  async created(){
    const token = '09d55adb458a02ab82b7584445af8294d4a7152b'
      await axios.get("https://api.brasil.io/v1/dataset/covid19/caso/data/?is_last=True&state=PB",{
      headers:{
        Authorization: `token ${token}`
      }
    }).then(function(response) {
      const data = response.data.results.forEach(element => {
          const city = element.city
          const confirmed = element.confirmed
          const deaths = element.deaths
          const state = element.state
          const pop = element.estimated_population

          console.log(`Cidade: ${city}`,
            `Quantidade de confirmados: ${confirmed}`,
            `Pop: ${pop}` ,
            `Quantidade de mortes ${deaths}`,
            `Estado: ${state}`)
      });
        
      console.log(data)
  }).catch(function (error) {
      if (error) {
          console.log(error)
      }
  })
  }
}
</script>

<style>

</style>
