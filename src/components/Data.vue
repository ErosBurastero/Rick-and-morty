<template>
  <div>
    <div class="d-flex justify-center"
    :class="{'d-flex justify-center' :$vuetify.breakpoint.smAndDown}" >
      <v-img
        class="photo"
        src="title1.png"
        max-height="500"
        max-width="600"
      ></v-img>
    </div>

    <div class="container">
      <v-card
        max-height="500"
        max-width="400"
        class="card my-5 ml-16"
        :class="{ 'd-flex justify-center': $vuetify.breakpoint.smAndDown }"
        elevation="2"
        v-for="(character, index) in characters"
        :key="index"
      >
        <v-img :src="character.image"></v-img>

        <div class="black darken-4 white--text title d-flex justify-center">
          {{ character.name }}
        </div>

        <div class="d-flex justify-center title green darken-4 white--text">
          {{ "CHARACTERISTICS:  " + character.status }} —
          {{ character.species }}
        </div>

        <div class="d-flex justify-center title light-blue darken-4">{{ "GENDER: " + character.gender }}</div>
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
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  gap: 10px 10px;
}

.card {
  border: solid grey 2px;
}
</style>
