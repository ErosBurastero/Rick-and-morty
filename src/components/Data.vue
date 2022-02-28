<template>
<div> 
    <v-card class="d-flex justify-center" max-width="500" max-height="500"  elevation="2" v-for="(character, index) in characters" :key="index">
      <div>  {{ character.name }}  </div> 
      <div> {{ character.status }} —  {{ character.species }} </div>
      <div></div>
      <v-divider></v-divider>
    </v-card>

</div>
  
</template>

<script>
export default {
    props: [
        'charactersData',
        
    ],

    data () {
        return {
            characters: [],
        }
    },

    methods: {
    fetchData() {
        let req = new Request(this.charactersData)
        fetch(req)
        .then((res => {
           return  res.json()
        }))

        .then((data) => {
            this.characters = data.results
        })

      
    }
    },

    created() {
        this.fetchData()
    }

    

}
</script>

<style>

</style>