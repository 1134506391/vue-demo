<template>
    <div>
        <select v-model="selectGrade" @chagne="chooseFn">
            <option v-for="item in defaultGradeData" :key="item.id" :value="item.id">{{item.name}}</option>
        </select>
    </div>
</template>

<script>
export default {
    props:['defaultGradeData'],
    data(){
        return{
            selectGrade:'',
            gradeData:[]
        }
    },
    methods:{
        initData(){
            this.gradeData = this.defaultGradeData
            this.selectGrade = this.gradeData[2].id
            this.$emit('choonseGrageEvent',this.selectGrade)
        },
        chooseFn(){
            this.$emit('choonseGrageEvent',this.selectGrade)
        }
    },
    created(){
        this.initData()
    }
}
</script>
