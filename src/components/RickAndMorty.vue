<template>
  <div>
      <Data :charactersData="charactersData" />
  </div>
</template>

<script>
import Data from './Data.vue'

export default {
    components: {
        Data,
    },

    data () {
        return { 
            charactersData: 'https://rickandmortyapi.com/api/character'
        }
    }
};
</script>

<style></style>
