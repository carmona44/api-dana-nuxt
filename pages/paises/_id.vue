<template>
  <div>
    <article>
      <h1>{{pais.id.toUpperCase()}}</h1>
      <h3>Latitud: {{pais.latitud}}</h3>
      <h3>Longitud: {{pais.longitud}}</h3>
      <h3>--------------------------------------</h3>
    </article>
    <aside>
      <h3>Otros países</h3>
      <ul>
        <li v-for="(pais, i) in otrosPaises" :key="`${i}-${pais.id}`">
          <nuxt-link :to="`/paises/${pais.id}`">{{pais.id}}</nuxt-link>
        </li>
      </ul>
    </aside>
  </div>
</template>

<script>
export default {
  data () {
    return {
      id: this.$route.params.id
    }
  },
  computed: {
    pais () {
      return this.$store.state.paises.all.find(sh => sh.id === this.id);
    },
    otrosPaises () {
      return this.$store.state.paises.all.filter(sh => sh.id !== this.id);
    }
  }
}
</script>