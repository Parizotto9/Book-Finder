<template >
 <div class="row justify-center">
  <Procura @passando-livros="livros = $event" />
  <Cards :livros = "livros"/>
  <q-sec >
    <footer class="text-h6 vertical-middle q-ma-md">Made by Daniel Parizotto</footer>
  </q-sec>
 </div>
</template>
<script>
import Procura from './components/Procura.vue'
import Cards from './components/Cards.vue'
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
  components: {Procura, Cards},
  data() {
    return {
      livros: []
    }
  }
})

</script>
<style >
@import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@1,300&display=swap');

q-sec {
  font-family: 'Lato', sans-serif;
}
</style>
