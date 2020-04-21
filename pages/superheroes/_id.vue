<template>
  <div>
    <article>
      <h1>{{superheroe.id.toUpperCase()}}</h1>
      <h3>Superpoder: {{superheroe.superpoder}}</h3>
      <h3>Debilidad: {{superheroe.debilidad}}</h3>
      <h3>--------------------------------------</h3>
    </article>
    <aside>
      <h3>Otros superheroes</h3>
      <ul>
        <li v-for="(otro, i) in otrosSuperheroes" :key="`${i}-${otro.id}`">
          <nuxt-link :to="`/superheroes/${otro.id}`">{{otro.id}}</nuxt-link>
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
    superheroe () {
      return this.$store.state.superheroes.all.find(sh => sh.id === this.id);
    },
    otrosSuperheroes () {
      return this.$store.state.superheroes.all.filter(sh => sh.id !== this.id);
    }
  }
}
</script>