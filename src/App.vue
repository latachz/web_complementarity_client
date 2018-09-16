<template>
<div class="container">
  <div class="jumbotron">
    <h1 class="display-4">DNA Complementarity App</h1>
    <p class="lead">This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.</p>
    <hr class="my-4">
    <form>
      <div class="form-group">
        <label for="dnaInput">Dna strand</label>
        <input v-model="dnaStrand"  type="text" class="form-control" id="dnaInput" aria-describedby="emailHelp" placeholder="ATCGTAATC">
      </div>
      <button @click="checkDna" type="submit" class="btn btn-primary">Check</button>
    </form>
  </div>

  <h1>{{ dnaStrand }}</h1>
  <h1>{{ newDnaStrand }}</h1>
</div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      dnaStrand: 'ATCGTAATC',
      newDnaStrand: 'TAGCATTAG'
    }
  },
  methods: {
    checkDna () {
      this.dnaStrand = this.dnaStrand
      this.newDnaStrand = this.dnaStrand
    }
  }
}
</script>

<style lang="scss">
body {
  background-color: #42b983;
}

h1, h2 {
  font-weight: normal;
  text-align: center;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
