<template>
  <div>
      <select v-model="selectSubject" @change="fnChose" >
          <option v-for="item in defaultSubjectData" :key="item.id"  :value="item.id">{{item.name}}</option>
      </select>
  </div>
</template>

<script>
export default {
props:['defaultSubjectData'],
  data () {
    return {
        subjectData:[],
        selectSubject:'',
    }
  },
  methods:{
      initData(){
         this.subjectData = this.defaultSubjectData
         this.selectSubject = this.subjectData[0].id
         this.$emit('chooseSubjectEvent',this.selectSubject) 
      },
      fnChose(){
         this.$emit('chooseSubjectEvent',this.selectSubject) 
      },
      reset(){
          this.selectSubject = this.subjectData[0].id
          this.$emit('chooseSubjectEvent',this.selectSubject) 
      }
  },
  created(){
      this.initData()
  }
}
</script>
