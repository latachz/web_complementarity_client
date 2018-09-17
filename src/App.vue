<template>
<div class="main">
<div class="container">
  <div class="jumbotron">
    <h1 class="display-4">DNA Complementarity App</h1>
    <p class="lead">Simple application which helps you in DNA Complementarity.</p>
    <hr class="my-4">
    <form>
      <div class="form-group">
        <label>Dna strand</label>
        <input autocomplete="off" style="text-transform:uppercase" v-model="dnaStrand" type="text" class="form-control" id="dnaInput" aria-describedby="emailHelp" placeholder="ATCGTAATC">
        <small class="form-text text-danger" v-if="error != ''">Nucleotides [A, C, T, G]</small>
      </div>
      <button @click="sendDna" type="button" class="btn btn-primary">Check</button>
    </form>
    <hr class="my-4">
    <h1 class="strand" v-if="error == ''">{{ dnaStrand.toUpperCase() }}</h1>
    <h1 class="strand">{{ newDnaStrand }}</h1>
  </div>

</div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'app',
  data () {
    return {
      dnaStrand: '',
      newDnaStrand: '',
      error: ''
    }
  },
  methods: {
    sendDna () {
      axios
        .post('http://localhost:4000/api/dna', {
          "strand": this.dnaStrand
        })
        .then((res) => {
            this.newDnaStrand = res.data
        })
        .catch(e => {
          this.error = e
        })
    }
  }
}
</script>

<style lang="scss">
.main {
  background: url(bg.jpg); 
  width: 100vw;
  height: 100vh;

}

button.btn {
  position: center;
}

.strand {

}

p.lead {
  text-align: center;
}

h1, h2 {
  font-weight: normal;
  text-align: center;
}

</style>
