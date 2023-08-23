<template>

 <select v-model="pageCount">
  <option value="5">5</option>
  <option value="10">10</option>
  <option value="15">15</option>
 </select> 

 <input type="text" v-model="user.first_name">
 <input type="text" v-model="user.last_name">

 <!--  <input type="text" v-model="name"><br>

  {{ name }}
 -->
<!--   {{ fullName }}

  <h2>Todos em aberto</h2>

  <div v-for="todo in uncompletedTodos" :key="todo.id">
    {{todo.title}} 
  </div>

  <h2>Todos Completas</h2>
  <div v-for="todo in completedTodos" :key="todo.id">
    {{todo.title}} 
  </div>
  <br>
  <div v-for="todo in todos" :key = "todo.id">
    <input id = "todo" type="checkbox" v-model="todo.completed"> 
    <label for="todo"> {{ todo.title }}</label>
 
  </div>
 -->
<!-- 
<form action="https:google.com" @submit.prevent="onSubmit">
  <button>Enviar</button>
</form> -->

 <!--  <div>
    One-way data binding<br>
    Two-way data binding<br>
    v-model -> formulários
  </div>

  <div>
    <label>Nome</label><br>
    <input v-model = "name" type="text"><br>
    {{ name }}
  </div>

  <div>
    <label>Sports</label><br>

    <select v-model = "sports" >
    <option value="">Escolha</option>
    <option value="futebol">Futebol</option>
    <option value="skate">Skate</option>
    <option value="tenis">Tenis</option>
  </select> <br>
  {{ sports }}
  </div>

  <div>
    <label>Cores</label><br>
    <input type="checkbox" v-model = "colors" value="azul">Azul<br>
    <input type="checkbox" v-model = "colors" value="amarelo">Amarelo<br>
    {{ colors }}
  </div> -->

  <!-- <div>
    <h1 :class = "{'title': false, 'title-Home': isHome}">
      Curso Vue 3
    </h1>
    <p :class="pClass">

      Lorem ipsum dolor sit amet consectetur adipisicing elit. Exercitationem officiis expedita adipisci distinctio veniam voluptatem suscipit perferendis, repudiandae explicabo, ad error iure totam! Dignissimos, perferendis. Porro dolore quas repudiandae qui!

    </p>

    <p :style="styleClass">

      Lorem ipsum dolor sit amet consectetur adipisicing elit. Exercitationem officiis expedita adipisci distinctio veniam voluptatem suscipit perferendis, repudiandae explicabo, ad error iure totam! Dignissimos, perferendis. Porro dolore quas repudiandae qui!

    </p>
  <div v-for="(obj, index) in todos" v-bind:key="obj.id" class="todos-item">
    
    <img v-if = "obj.imgSrc" v-bind:src="obj.imgSrc">
    
    {{index}} - {{ obj.title }}
  </div> -->
  <!-- <TheHeader v-if="showHeader" />

  <div v-show="showName">
    Nome: {{ firstName }}
    Sobrenome : {{ lastName }}
  </div>

  <div v-if="accessLevel === 'admin'">Admin</div>
  <div v-else-if="accessLevel === 'marketing'">Marketing</div>
  <div v-else>User</div>

  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App" />
 -->
 </template>

<script>
/* import HelloWorld from './components/HelloWorld.vue'
import TheHeader from './components/TheHeader'
 */
export default {
  name: 'App',
  /* components: {
    HelloWorld,
    TheHeader,
  }, */
  data() {
    return {
      user:{
        first_name: 'saulo',
        last_name: 'bruno'
      },
      pageCount:5,
      name:'jon snow',
      colors: [],
      sports: 'skate',
      classVar: 'title',
      isHome: true,
      pClass: ['text', 'text-home'],
      styleClass: {color: 'aqua', backgroundColor:'black', 'font-size': '30px'},
      todos: [
        {
          "userId": 1,
          "id": 1,
          "title": "delectus aut autem",
          "completed": false,
          "imgSrc": "https://placehold.co/150x150"
        },
        {
          "userId": 1,
          "id": 2,
          "title": "quis ut nam facilis et officia qui",
          "completed": false,
          "imgSrc": "https://placehold.co/150x150"
        },
        {
          "userId": 1,
          "id": 3,
          "title": "fugiat veniam minus",
          "completed": false
        },
        {
          "userId": 1,
          "id": 4,
          "title": "et porro tempora",
          "completed": true
        },
        {
          "userId": 1,
          "id": 5,
          "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
          "completed": false
        }
      ],
     /*  showHeader: true,
      firstName: 'Jon',
      lastName: 'Snow',
      showName: false,
      accessLevel: 'user'
      */
    } 
  },
  methods:{
    onClick($evt){
      console.log('click', $evt);
    },
    onSubmit(){
      console.log('submit');
    },
    saveUserName(){
      console.log('Ajax');
      console.log(this.name);
    },
    changePage(){
      console.log('Ajax changepage');
    }

  },
  watch:{
    name(v1){
      if(v1.length >= 3){
        this.saveUserName();
      }
    },
    pageCount(){
      this.changePage();
    },
    user:{
      handler(){
        console.log('user alterado')
      },
      deep:true
    }
  },
  computed:{
    fullName(){
      return `${this.user.first_name} ${this.user.last_name}`
    },
    uncompletedTodos(){
      return this.todos.filter(todo => !todo.completed);
    },
    completedTodos(){
      return this.todos.filter(todo => todo.completed);
    }

  }
}
</script>

<style>
.title {
  font-size: 20px;
  color:blue;
}
.title-home {
  font-size: 40px;
  color:green;
}
.text{
  color:yellow;
  font-size: 40px;
}

.text-home{
  color: green;
}

.todos-item {
  background: #000;
  margin: 0 0 5px 0;
  padding: 3px 6px;
  color: #fff;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
