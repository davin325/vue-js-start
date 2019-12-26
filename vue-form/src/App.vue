<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <!-- label의 for는 어떤 태그를 위한 label인지 표시 -->
      <!-- label 클릭시 input에 자동으로 포커싱 -->
      <!-- v-model form에서 주로 사용되는 속성
      폼에 입력한 값과 뷰 인스턴스의 데이터를 즉시 동기화
      <inpt> <select> <textarea>에서만 사용 가능-->
      <label for="username">id:</label>
      <input id="username" type="text" v-model="username" />
    </div>
    <div>
      <label for="password">pw:</label>
      <input id="password" type="password" v-model="password" />
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      username: "",
      password: ""
    };
  },
  methods: {
    submitForm: function() {
      // e.preventDefault(); 바닐라 JS, JQuery방법 Vue에서는 v-on:submit.prevent
      window.console.log(this.username, this.password);
      var url = "https://jsonplaceholder.typicode.com/users";
      var data = {
        username: this.username,
        password: this.password
      };

      axios
        .post(url, data)
        //성공시 호출
        .then(function(response) {
          window.console.log(response);
        })
        //실패시 호출
        .catch(function(error) {
          window.console.log(error);
        });
    }
  }
};
</script>

<style>
</style>