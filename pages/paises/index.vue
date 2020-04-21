<template>
  <div>
    <h1>Países</h1>
    <h3>A continuación te dejamos el listado de los países presentes en nuestra API:</h3>
    <ul>
        <li v-for="(pais, i) in paises" :key="`${i}-${pais.id}`">
            <nuxt-link :to="`/paises/${pais.id}`">{{pais.id}}</nuxt-link>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
    computed: {
        paises () {
            return this.$store.state.paises.all;
        }
    }
}
</script>