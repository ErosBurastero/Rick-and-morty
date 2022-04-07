<template>
  <div>
    <div class="d-flex justify-center"
    
    >
      <v-img
        :class="{'d-flex justify-center':$vuetify.breakpoint.smAndUp}"
        class="photo"
        src="title1.png"
        max-height="400"
        max-width="300"
      ></v-img>

    </div>

    <div class="d-flex justify-center flex-wrap"
    >
      <v-card
        
        max-width="700"
        class="ml-2 pa-10 my-5 light-blue accent-3"
        :class="{'d-flex justify-center':$vuetify.breakpoint.smAndUp}"
        elevation="2"
        v-for="(character, index) in characters"
        :key="index"
      >
        <v-img max-height="300" max-width="350" :src="character.image"></v-img>

    <div class="ml-16">
          <div class=" black--text   display-1 font-italic">
          {{ character.name }}
        </div>

        <v-divider></v-divider>

        <div class="title my-4 ml-3">CHARACTERISTICS: <br>
         <div class="ml-6">  {{  character.status }} —
          {{ character.species }}</div>  
        </div>

        <v-divider></v-divider>
        

        <div class="title ml-8 my-4 ">{{ "GENDER: " + character.gender }}</div>
    </div>
    
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  props: ["charactersData"],

  data() {
    return {
      characters: [],
    };
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

 
</style>
