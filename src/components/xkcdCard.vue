<template>
  <v-flex xs6>
    <v-card>
      <v-card-title>
        <h1>{{xkcd.title}}</h1>
        <div class='date blue-grey--text'>{{xkcd.month}}/{{xkcd.day}}/{{xkcd.year}}</div>
      </v-card-title>
      <v-img :src='xkcd.img'></v-img>
      <div class='altText'>{{xkcd.alt}}</div>
      <v-btn flat color='accent' @click='viewXkcd(xkcd.num)'>View</v-btn>
      <v-btn flat color='accent' @click='explainXkcd(xkcd.num)'>Explain</v-btn>
    </v-card>
  </v-flex>
</template>

<script>
export default {
  name: 'xkcdCard',
  props: {
    xkcd: Object
  },
  methods: {
    viewXkcd(num) {
      window.open('https://www.xkcd.com/' + num);
    },
    explainXkcd(num) {
      window.open('https://www.explainxkcd.com/' + num);
    }
  }
}
</script>

<style scoped>
.xkcdCard {

}
.date {
  margin-left: 1em;
  margin-right: 1em;
}
.altText {
  margin-top: 1em;
  margin-right: 1em;
  margin-left: 1em;
}
</style>
