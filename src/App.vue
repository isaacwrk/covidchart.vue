<template>
  <div class="id">

  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'App',
  components: {
    
  },
  async created(){
    const token = '09d55adb458a02ab82b7584445af8294d4a7152b'
    const { data } = await axios.get("https://api.brasil.io/v1/dataset/covid19/caso/data/?is_last=True&state=PB",{
      headers:{
        Authorization: `token ${token}`
      }
    })
    console.log(data)
}
}
</script>

<style>

</style>
