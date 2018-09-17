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
   <div class="footer">
      <div class="container">
        <p class="font-weight-bold">Created<i class="fa fa-html5" aria-hidden="true"></i> <i class="fa fa-css3" aria-hidden="true"></i> by <a href="http://kacperlatuszewski.pl" target="_blank"><em><b>Kacper Latuszewski</b></em></a></p>
        <p class="font-weight-bold">You can find this project there! <a href="https://github.com/latachz">GitHub</a></p>
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
        .post('https://complementarity-dna-api.herokuapp.com/api/dna', {
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
  color: black;
}

.footer {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  background-color: black;
  text-align: center;
  height: 120px;
  padding: 25px;
  color: white;

}

button.btn {
  position: center;
}

p.lead {
  text-align: center;
}

h1, h2 {
  font-weight: normal;
  text-align: center;
}

</style>
