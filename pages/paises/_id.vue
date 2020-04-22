<template>
  <div>
    <p v-if="$fetchState.pending">Fetching paises...</p>
    <p v-else-if="$fetchState.error">Error while fetching paises: {{ $fetchState.error.message }}</p>
    <div v-else>
      <article>
        <h1>{{pais.name}}</h1>
        <h3>Latitud: {{pais.latitude}}</h3>
        <h3>Longitud: {{pais.longitude}}</h3>
        <h3>--------------------------------------</h3>
      </article>
      <aside>
        <h3>Otros países</h3>
        <ul>
          <li v-for="(pais, i) in otrosPaises" :key="`${i}-${pais._id}`">
            <nuxt-link :to="`/paises/${pais._id}`">{{pais.name}}</nuxt-link>
          </li>
        </ul>
      </aside>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      id: this.$route.params.id,
      paises: [],
      pais: {}
    }
  },
  head () {
    return {
      title: `${this.pais.name} | Probando`,
      meta: [
        { name: 'description', content: this.id }
      ]
    }
  },
  computed: {
    otrosPaises () {
      return this.paises.filter(sh => sh._id !== this.id);
    }
  },
  async fetch() {
      this.paises = await this.$http.$get(`http://localhost:3000/country`);
      this.pais = await this.$http.$get(`http://localhost:3000/country/${this.id}`);
  }
}
</script>