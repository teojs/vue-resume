<template>
  <div class="content">
    <Loading :already='already'></Loading>
    <asideLeft v-show='already'>
      <Banner :username='username' :jobType='jobType'></Banner>
      <baseInfo :baseInfo='baseInfo' :skills='skills'></baseInfo>
    </asideLeft>
    <asideRight v-show='already' :workExperience='workExperience' :careerObjective='careerObjective' :eduExperience='eduExperience' :projectExperience='projectExperience' :relatedWorks='relatedWorks'></asideRight>
  </div>
</template>
<script>
import Loading from './components/Loading.vue'
import asideLeft from './components/Aside-left.vue'
import asideRight from './components/Aside-right.vue'
import Banner from './components/Banner.vue'
import baseInfo from './components/Base-info.vue'

export default {
  name: 'app',
  components: {
    Loading,
    asideLeft,
    asideRight,
    Banner,
    baseInfo
  },
  data() {
    return {
      already: false,
      username: '',
      jobType: '',
      baseInfo: [],
      skills: [],
      workExperience: [],
      careerObjective: [],
      eduExperience: [],
      projectExperience: [],
      relatedWorks: [],
    }
  },
  mounted() {
    this.$nextTick(function() {
      this.getResumeData();
      this.hideLoading();
    })
  },
  methods: {
    getResumeData: function() {
      this.$http.get('./static/resume.json').then((data) => {
      	if (data.body.status == "0") {
	        this.username = data.body.userName
	        this.jobType = data.body.jobType
	        this.baseInfo = data.body.baseInfo
	        this.skills = data.body.skills
	        this.workExperience = data.body.workExperience
	        this.careerObjective = data.body.careerObjective
	        this.eduExperience = data.body.eduExperience
	        this.projectExperience = data.body.projectExperience
	        this.relatedWorks = data.body.relatedWorks
      	} else{
      		alert('数据获取失败！')
      	}
      })
    },
    hideLoading: function() {
      setTimeout(() => {
        this.already = true
      }, 2000)
    }
  }
}
</script>
<style src="./assets/styles/main.scss" lang='scss'></style>
