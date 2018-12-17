<template>
  <div class="hello">
   <com-subject ref="subject" v-on:chooseSubjectEvent="changeSubject"  :defaultSubjectData="defaultSubjectData"></com-subject>
   {{subjectId}}
   <div @click="resetBtn">重置</div>
  </div>
</template>

<script>
import comSubject from './comSubject'
export default {
  components:{
    comSubject
  },
  data () {
    return {
      defaultSubjectData:[{"id":12,"name":"语文"},{"id":13,"name":"数学"},{"id":16,"name":"英语"},{"id":17,"name":"化学"},{"id":18,"name":"物理"}],
      subjectId:'',
    }
  },
  methods:{
    changeSubject(subject){
      this.subjectId = subject
    },
    resetBtn(){
      this.$refs.subject.reset()
    }
  }
}
</script>


