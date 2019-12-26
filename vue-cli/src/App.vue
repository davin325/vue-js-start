<template>
  <div>
    <!-- <app-header v-bind:프롭스 속성 이름="상위 컴포넌트의 데이터 이름"></app-header> -->
    <app-header v-on:renew="renewStr" v-bind:propsdata="str"></app-header>
  </div>
</template>

<script>
//AppHeader 변수에 components 담음
import AppHeader from "./components/AppHeader.vue";

export default {
  data: function() {
    return {
      str: "Header"
    };
  },
  components: {
    "app-header": AppHeader
  },
  methods: {
    renewStr: function() {
      this.str = "hihi";
    }
  }
};
</script>

<style>
</style>