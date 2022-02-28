<template>
  <v-app>
 
    <v-main>
          <RickAndMorty />

    </v-main>
  </v-app>
</template>

<script>
import RickAndMorty from './components/RickAndMorty.vue';

export default {
  name: 'App',

  components: {
    RickAndMorty,
  },

  data: () => ({
    //
  }),
};
</script>
