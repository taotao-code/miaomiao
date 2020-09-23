<template>
  <div class="home">
    <UcBanner  :data="banner"
      collectionName="banner"
      />
	  <div class="list">
      <UcCell 
	   v-for="(item,index) of list"
        :key="item._id"  
		:data="item" 
		:index=index 
		collectionName="home"/>
	  </div>
  </div>
</template>

<script>
	import axios from "axios"
	import Header from "../layouts/header.vue"
	import Footer from "../layouts/Footer.vue"
	import UcBanner from "../components/uc-banner/uc-banner.vue"
	import UcCell from "../components/uc-cell/uc-cell.vue"
  export default {
    name:'home',
    props:{},
   data(){
     return {
       banner:[],
       list:[]
     }
   },
    components:{UcBanner,UcCell,Header,Footer},
    mounted(){
		this.$axios({
		  url:'/api/home',
		  params:{_limit:20,_page:1}
		}).then(
		  res => this.list = res.data.data
		)
		
		this.$axios({
		  url:'/api/banner',
		  params:{_limit:3,_page:1}
		}).then(
		  res => this.banner = res.data.data
		)
	},
    updated(){},
    methods:{}
  }
</script>

<style scoped>
  .home{
	  padding-bottom: 0.8rem;
  }
  .list{
    padding-left:0.34rem;padding-right: 0.34rem;
  }
</style>
