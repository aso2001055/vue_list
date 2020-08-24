<template>
  <div id="app">
    <MyList v-bind:title="message"
    v-on:result-event="appAction" />
    <hr>
    <div><table v-html="log" align="center"></table></div>
  </div>
</template>

<script>
import MyList from './components/MyList.vue'
export default {
  name: 'app',
  components: {
    MyList
  },
  data:function(){
    return {
      message:"メモを入力してください",
      mylist:[],
      cnt:0,
    };
  },
  computed:{
    log:function(){
      var table="<tr><th class='head'>My List</th></tr>";
      for(var i in this.mylist){
        table += "<tr><td>"+this.mylist[i]+"</td></tr>";
      }
      return table;
    }
  },
  created:function(){
    
  },
  methods:{
    appAction:function(input_text){
      this.mylist.unshift(input_text);
      this.cnt++;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
tr td{
  padding:5px;
  border:1px solid gray;
}
th tr{
  padding:5px;
  border:1px solid gray;
}
tr th.head{
  background-color:black;
  color:white;
}
</style>
