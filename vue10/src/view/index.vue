<template>
    <div class="hello">
      <!-- <div v-on:click="openBtn"></div> -->
      <com-grade ref="grade" v-on:choonseGrageEvent="changeGrade" :defaultGradeData="defaultGradeData"></com-grade>
      {{gradeId}}
      <button @click="gradeInit">gradeInit</button>
    </div>
  </template>
  
  <script>
  import comGrade from '../components/comGrade'
  export default {
    components:{
      comGrade
    },
    data () {
      return {
        defaultGradeData:[{"id":1,"name":"一年级"},{"id":2,"name":"二年级"},{"id":3,"name":"三年级"}],
        gradeId:'',
      }
    },
    methods:{
      changeGrade(grade){
        this.gradeId = grade
      },
      gradeInit(){
        this.$refs.grade.initData()
      },
    },
  }
  </script>
  