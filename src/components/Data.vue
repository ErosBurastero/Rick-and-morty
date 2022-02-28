<template>
<div> 
    <div v-for="(rick, index) in characters" :key="index">
        {{ rick.name }}
    </div>

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
        .then((resp => {
            if (resp.status === 200) {
                return resp.json()
            }
        }))

        .then((data => {
            this.characters = data.props
            data.results.forEach(rick => {
                rick.id = rick.url
               
                this.characters.push(rick)
            });
        }))
    }
    },

    created() {
        this.fetchData()
    }

    

}
</script>

<style>

</style>