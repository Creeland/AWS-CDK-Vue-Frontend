<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="email" v-on:keyup.enter="addEmail" ref="email"/>
    <button @click="addEmail">Submit</button>
  </div>
</template>

<script>
const {v4: uuid} = require("uuid")

// Include your endpoint here 
const apiEndpoint = "";

export default {
  name: 'EmailForm',
  methods: {
    addEmail: function() {
      const newEmail = { email: this.$refs.email.value, id: uuid() };
      if (!apiEndpoint) return;
      fetch(apiEndpoint, {
          method: "POST",
          body: JSON.stringify(newEmail)
      });
    }
  },
  props: {
    msg: String
  },
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
