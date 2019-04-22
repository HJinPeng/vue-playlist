<template>
  <div id="home">
    <app-header @titleChanged="updateTitle($event)"  :title="title"></app-header>
    <users v-bind:users="users"></users>
    <users v-bind:users="users" ></users>
    <app-footer :title="title"></app-footer>
  </div>
</template>

<script>
import HelloWorld from './HelloWorld'
//局部注册组件
import Users from './Users'
import Header from './Header'
import Footer from './Footer'

export default {
  name: 'home',
  data() {
    return {
      //title: "this is my first vue-cli"
      users:[
            // {name:"xiaoming",position:"web开发",show:false},
            // {name:"xiaoming",position:"web开发",show:false},
            // {name:"xiaoming",position:"web开发",show:false},
            // {name:"xiaoming",position:"web开发",show:false},
            // {name:"xiaoming",position:"web开发",show:false},
            // {name:"xiaoming",position:"web开发",show:false},
            // {name:"xiaoming",position:"web开发",show:false},
            // {name:"xiaoming",position:"web开发",show:false},
            // {name:"xiaoming",position:"web开发",show:false}
        ],
      title:"传递的是一个值,number string boolean",
    }
    
  },
  methods:{
    updateTitle(title){
      this.title = title;
    }
  },
  components:{
    "users": Users,
    "app-header":Header,
    "app-footer":Footer
  },
  created(){
      this.$http.get("http://jsonplaceholder.typicode.com/users").then((data) => {
        //   console.log(data);
        this.users = data.body;
      }).catch((err) => {
          
      });
  }
}
</script>

<style>
h1{
  color:purple;
}
</style>
