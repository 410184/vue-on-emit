<template>
  <div id="app">    
    <h1 v-html="mag">{{mag}}</h1>
    <!-- @keyup.enter="submit" -->
    <input type="text" @keyup.enter="addItem" v-model="newItem">
    <ul>
      <li v-for="(item,index) in items" :key="index" :class="[firstClass,{listClass:item.isFinshed,lastClass:item.isFinshed}]">
         {{item.label}}
      </li>
    </ul>
    方法 1 
     <hello-world fatherSong="APP tell" v-on:childTell='listen'></hello-world>
    APP : {{childSong}} 
    
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
export default {
  name: 'App',
  components:{
    HelloWorld,
  },
  data(){
    return {
      newItem:'',
      mag:"<b>hello</b>你好",
      items:[
        {
          label:'coding',
          isFinshed:false,
        },
        {
          label:'working',
          isFinshed:true,
        },
      ],
      firstClass:"firstClass",
      lastClass:"aaa",
      childSong:"",
    }
  },
  watch:{

  },
  events:{
    'childTell':function(data){
      console.log(data);
      this.childSong=data
    }
  },
  methods:{
    addItem(){
      this.items.push({
        label:this.newItem,
        isFinshed:true
      })
      this.newItem="";
    },
    
    listen(data){
      this.childSong=data;
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
.firstClass{
  list-style: none;
}
</style>
