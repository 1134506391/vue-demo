<template>
  <div class="hello">
    <div>
         <com-subject ref="subject" v-on:chooseSubjectEvent="changeSubject"  :defaultSubjectData="defaultSubjectData"></com-subject>
         {{subjectId}}
         <button @click="resetBtn">重置</button>
    </div>
    <ul>
      <li v-for="(item,index) in cnodeData" :key="item.id">{{index+1}}--{{item.title}}</li>
    </ul>
    <com-grade ref="grade" v-on:choonseGrageEvent="changeGrade" :defaultGradeData="defaultGradeData"></com-grade>
    {{gradeId}}
    <button @click="gradeInit">gradeInit</button>
  </div>
</template>

<script>
import comSubject from './comSubject'
import comGrade from './comGrade'
import axios from 'axios'
export default {
  components:{
    comSubject,
    comGrade
  },
  data () {
    return {
      defaultGradeData:[{"id":1,"name":"一年级"},{"id":2,"name":"二年级"},{"id":3,"name":"三年级"}],
      defaultSubjectData:[{"id":2,"name":"语文"},{"id":3,"name":"数学"},{"id":6,"name":"英语"},{"id":7,"name":"化学"},{"id":8,"name":"物理"}],
      subjectId:'',
      cnodeData:[],
      page:1,
      gradeId:'',
    }
  },
  methods:{
    changeSubject(msg){
      console.log(msg)
      this.subjectId = msg
    },
    resetBtn(){
      this.$refs.subject.initData()
    },
    changeGrade(grade){
      this.gradeId = grade
    },
    gradeInit(){
      this.$refs.grade.initData()
    },
    getCnodeData(){
      axios.get('https://cnodejs.org/api/v1/topics',{
        params:{
          limit:10,
          page:this.page
        }
      })
          .then(response => {
            console.log(response.data.data)
            this.cnodeData = response.data.data;
          })
          .catch(error => {
            console.log(error)
          })
    }
  },
  created(){
    this.getCnodeData()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

