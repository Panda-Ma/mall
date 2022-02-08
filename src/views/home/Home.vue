<template>
  <div class="home">
    <nav-bar class="home-nav">
      <template v-slot:center>
        <div>购物街</div>
      </template>
    </nav-bar>
    <HomeSwiper :banners="banners" class="homeSwiper"></HomeSwiper>
    <RecommendView :recommends="recommends"/>
  </div>
  <h2>首页</h2>

</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import HomeSwiper from "views/home/childComps/HomeSwiper";
import {getHomeMultidata} from "@/network/home";
import RecommendView from "views/home/childComps/RecommendView";

export default {
  name: "home",
  components: {RecommendView, NavBar,HomeSwiper},
  data(){
    return {
    banners:[],
    recommends:[]
    }
  },
  created() {
    getHomeMultidata().then((res)=>{
      console.log(res);
      this.banners = res.data.banner.list;
      this.recommends=res.data.recommend.list
    })
  }
}
</script>

<style scoped>
.home-nav{
  background-color: var(--color-tint);
  color:#fff;
}
.homeSwiper{
/*height: 100px;*/
}
</style>