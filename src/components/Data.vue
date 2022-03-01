<template>
  <div class="container ">
    
      
    <v-card
      max-height="500"
      max-width="400"
      class="my-5 ml-16"
      elevation="2"
      v-for="(character, index) in characters"
      :key="index"
    >
      <v-img :src="character.image"></v-img>

      <div >
        <div class="brown darken-4 white--text title d-flex justify-center">{{ character.name }}</div>
        
        <div class="ml-14 ">{{ "CHARACTERISTICS:  " + character.status }} — {{ character.species }}</div>
        
        <div>{{ character.gender }}</div>
      </div>
    </v-card>
  </div>
</template>

<script>
export default {
  props: ["charactersData"],

  data() {
    return {
      characters: [],
    }
  },

  methods: {
    fetchData() {
      let req = new Request(this.charactersData);
      fetch(req)
        .then((res) => {
          return res.json();
        })

        .then((data) => {
          this.characters = data.results;
        });
    },

  
  },


  created() {
    this.fetchData();
  },
};
</script>

<style>


.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  gap: 10px 10px;
}
</style>
