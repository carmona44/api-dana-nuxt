<template>
  <div>
    <div>
        <h1>Superheroes</h1>
        <h3>A continuación te dejamos el listado de los superheroes presentes en nuestra API:</h3>
        <ul>
            <li v-for="(sh, i) in superheroes" :key="`${i}-${sh.id}`">
                <nuxt-link :to="`/superheroes/${sh.id}`">{{sh.id}}</nuxt-link>
            </li>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
    computed: {
        superheroes () {
            return this.$store.state.superheroes.all;
        }
    }
}
</script>