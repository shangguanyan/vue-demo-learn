<template>
  <div class="hello">
    <h1>{{msg}}</h1>
      <span>{{childvalue}}</span>
      <input type="button" value="点击触发" v-on:click="childDo" />
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      childvalue: 'this is child value'
    }
  },
  props: {
    msg: String
  },
  methods: {
    childClick: function(){
      this.$emit('chiByChild',this.childvalue)
    },
    childDo (){
      this.$emit('chiByChild',this.childvalue)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
