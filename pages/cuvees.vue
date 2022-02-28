<template>
  <div>
    <v-carousel v-model="model">
      <v-carousel-item v-for="(article, i) in articles" :key="i">
        <v-sheet height="100%" tile>
          <v-row class="fill-height" align="center" justify="center">
            <div class="text-h2">
              <h5 align="center">{{ article.name }}</h5>
              <div align="center">
                <img :src="article.image" width="250px" align="center" />
              </div>
              <p class="text-description">{{ article.description }}</p>
            </div>
          </v-row>
        </v-sheet>
      </v-carousel-item>
    </v-carousel>
    <v-spacer></v-spacer>
    <v-container>
      <v-flex xs12 pb-3>
        <h1>Nos Cuvées</h1>
      </v-flex>
      <v-flex v-for="(article, index) in articles" :key="index">
        <v-card class="mx-auto" max-width="350" pb-3>
          <img :src="article.image" width="200px" />
          <!-- <img :src="article.composition" width="200px" /> -->
          <v-card-title> {{ article.name }} </v-card-title>
          <v-divider></v-divider>
          <v-card-text>
            {{ article.description }}
          </v-card-text>
        </v-card>
      </v-flex>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'NosCuvees',
  async asyncData({ app }) {
    const { articles } = await app.$axios.$get(
      'https://gist.githubusercontent.com/Aphideth/82247cbaf15f1fcef3bde2ad5b4fb148/raw/d394d6e51b7f35707abf88e6b695dee4419c5473/champagne.json'
    )
    return { articles }
  },
}
</script>

<style>
.text-description {
  font-size: 18px;
}
</style>
