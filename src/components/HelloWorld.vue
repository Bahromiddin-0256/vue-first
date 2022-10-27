<template>
  <div class="hello">
    {{ objectID }}
  </div>
  <HelloWorld />
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      listProducts:[],
      objectID: null,
      metadataDate: new Date(),
    }
  },
  mounted() {
    this.getProducts();
    console.log()
  },
  methods: {
    async getProducts(){

      this.listProducts = [1,2,3,4]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
