<template>
<div class=" fit " >
  <h3 class="fonte row justify-center">Book Finder</h3>
  <div class="row justify-center " >
    <q-input outlined v-model="procurar" label="Book" 
        color="purple"
        class=" input col-md-4 "  >
      <template v-slot:prepend>
        <q-icon name="menu_book " />
      </template>
    </q-input>
    <q-btn icon="search" round  color="deep-purple-6" class="q-ml-md self-center" @click="find()"/>
  </div>
</div>
</template>

<script>
import api from '../axios'


export default {
  data () {
    return {
      procurar: '',
      livros: [],
      infoCompleta: [],
    }
  },
  methods: {
    find () {
      this.livros = []
       api.get(`${this.procurar}`).then(res => {
        this.infoCompleta = res.data

        for (let livro in this.infoCompleta.items ) {
            this.$data.livros.push ({
                "Title" : this.infoCompleta.items[livro].volumeInfo.title,
                "Author" : this.infoCompleta.items[livro].volumeInfo.authors,
                "PublishedDate" : this.infoCompleta.items[livro].volumeInfo.publishedDate,
                "Image" :  this.infoCompleta.items[livro].volumeInfo.imageLinks.thumbnail,
                "Link" : this.infoCompleta.items[livro].volumeInfo.infoLink,
            })
        }
      })
      this.$emit('passando-livros', this.livros)
    }
  }

}

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Londrina+Shadow&display=swap');

.fonte {
  font-family: 'Londrina Shadow', cursive;
}
</style>
