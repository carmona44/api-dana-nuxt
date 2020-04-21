<template>
  <div>
    <h1>Países</h1>
    <h3>A continuación te dejamos el listado de los países presentes en nuestra API:</h3>
    <p v-if="$fetchState.pending">Fetching paises...</p>
    <p v-else-if="$fetchState.error">Error while fetching paises: {{ $fetchState.error.message }}</p>
    <ul v-else>
        <li v-for="(pais, i) in paises" :key="`${i}-${pais._id}`">
            <nuxt-link :to="`/paises/${pais._id}`">{{pais.name}}</nuxt-link>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
    data(){
        return {
            paises: []
        }
    },
    head (){
        return {
            title: 'Paises | Probando',
            meta: [
                { name: 'description', content: 'Listado de paises' }
            ]
        }
    },
    async fetch() {
        this.paises = await this.$http.$get('http://localhost:3000/country');
    }
}
</script>