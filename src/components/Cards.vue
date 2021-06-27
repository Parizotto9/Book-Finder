<template>
  <div class="fit row justify-center"  > 
    <q-container class="row col-md-6 ">

      <q-card class="my-card q-ma-xl " v-for="livro in livros" :key="livro"> 
      <q-img :src="livro.Image" />

      <q-card-section>
        <q-btn
          fab
          color="primary"
          icon="info"
          class="absolute"
          style="top: 0; right: 12px; transform: translateY(-50%);"
          @click="abrir(livro.Link)"
        />

        <div class="row no-wrap items-center">
          <div class="col text-h6 ellipsis">
            {{ livro.Title }}
          </div>

        </div>

      </q-card-section>

      <q-card-section class="q-pt-none">
        <div class="text-subtitle1">
          {{ livro.Author[0] }}
        </div>
        <div class="text-caption text-grey">
          {{ livro.PublishedDate }}
        </div>
      </q-card-section>
    </q-card>
    {{  }} 
    </q-container>
  </div>
</template>

<script>


export default {
  props: {livros : Array},
  data(){
    return {
      imagi: "https://cdn.quasar.dev/img/chicken-salad.jpg"
    }
  },
  methods: {
    abrir(link) {
      window.open(link, '_blank')
    }
  }
}

</script>

<style scoped>
.my-card {
  width: 100%;
  max-width: 250px
}

div {
  font-weight: 600;
  font-size: 1.2rem;
  font-family: 'Benne', serif;
}

@import url('https://fonts.googleapis.com/css2?family=Benne&display=swap');

</style>