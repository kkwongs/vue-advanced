<template>
  <div>
    <button @click="loginUser1">login</button>
    <h1>List</h1>
    <ul>
      <li v-for="item in items" v-bind:key="item">{{ item }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import { handleException } from './utils/handler.js';

export default {
  data() {
    return {
      items: [],
    }
  },
  methods: {
    loginUser() {
      axios.get('https://jsonplaceholder.typicode.com/users/1')
        .then(response => {
          if(response.data.id === 1) {
            console.log("사용자가 인증되었습니다.");
            axios.get('https://jsonplaceholder.typicode.com/todos')
              .then(response => {
                this.items = response.data;
              });
          }
        })
        .catch(error => console.log(error));
    },
    async loginUser1() {
      try {
        var response = await axios.get('https://jsonplaceholder.typicode.com/users/1');
        if(response.data.id === 1) {
          console.log("사용자가 인증되었습니다.");
          var list =  await axios.get('https://jsonplaceholder.typicode.com/todos');
          this.itmes = list.data;
        }
      } catch (error) {
        // 공통 에러 처리 함수
        handleException(error);
        console.log(error);
      }
    }
  },
}
</script>

<style>

</style>