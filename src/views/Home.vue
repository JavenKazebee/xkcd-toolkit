<template>
  <v-container grid-list-lg>
    <v-layout v-for='comic in comics' row justify-center>
      <xkcdCard :xkcd='comic'></xkcdCard>
    </v-layout>
  </v-container>
</template>

<script>
import xkcdCard from '@/components/xkcdCard.vue';
import axios from 'axios';

export default {
  data() {
    return {
      comics: []
    }
  },
  components: {
    xkcdCard
  },
  methods: {
    loadComic(num) {
      axios.get('https://xkcd.now.sh/' + num).then(res => (this.comics.push(res.data)));
    },
    loadLatestComic() {
      axios.get('https://xkcd.now.sh').then(res => (this.comics.push(res.data)));
    },
    loadComics(base, num) {
      var requests = [];
      var response;
      for(var i = 0; i < num; i++) {
        requests.push(axios.get('https://xkcd.now.sh/' + (base - i)));
      }
      axios.all(requests).then(this.handleResponse(res));
    },
    handleResponse(res
    ) {
      console.log(res);
    }
  },
  mounted: function() {
    this.loadComics(1000, 5);
  }
}
</script>
