<template>
  <div class="coumn pd-top">
   <UcCell 
	v-for="(item,index) of list"
     :key="item._id"  
	 :data="item"  
	 collectionName="column"/>
  </div>
</template>

<script>
	import UcCell from "../components/uc-cell/uc-cell.vue"
	import Header from "../layouts/header.vue"
	import Footer from "../layouts/Footer.vue"
  export default {
    name:'coumn',
    props:{},
    data(){
      return {
        list:[]
      }
    },
    components:{UcCell,Header,Footer},
    mounted(){
		this.$axios({
			url:"/api/home",
			params:{_limit:10,_page:1},
		}).then(
			res=>this.list=res.data.data
		)
	},
    updated(){},
    methods:{}
  }
</script>

<style scoped>
  .coumn{padding-left:0.34rem;padding-right:0.34rem; padding-bottom: 0.8rem;}
</style>
