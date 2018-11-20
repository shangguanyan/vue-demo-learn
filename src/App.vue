<template>
  <div id="app">
    <h1 v-html="msg"></h1>
    <input type="text" name="addItem" v-model="itemNew" placeholder="addItem" @keyup.enter="addItem" />
    <div>
      <span>
        {{valueFromChild}}
      </span>
    </div>
      <div v-for="item in items"  @click="trunOver(item)" class="static" :class={overtype:item.status}>
          {{item.name}}
      </div>

      <!-- <hello :msg="msgChild"></hello>   -->
      <hello v-on:chiByChild="chiByChild" :msg="msgChild"></hello>
  </div>
</template>

<script>
  import hello from './components/hello'
  export default {
    name :'app',
    components:{
      hello
    },
    data () {
      return {
        msg: "hello world",
        items:[],
        itemNew:'',
        msgChild:'child',
        valueFromChild:''
      }
    },
    methods: {
      addItem :function(){
        this.items.push({
            name: this.itemNew,
            status: false
            }
          );
        this.msgChild = this.itemNew;
        deep:true;
        this.itemNew = ''
      },
      trunOver :function(item){
          item.status = !item.status
      },
      chiByChild :function(childvalue){
        this.valueFromChild = childvalue
      }
    }
  }
  
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.overtype{
  text-decoration: line-throungh;
  color: blue
}
.static{
  padding-top: 4px;
  font-size: 21px;
}
</style>
