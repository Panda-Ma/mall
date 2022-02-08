<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>
    <!-- 图片active插槽 -->
    <div v-else>
      <slot name="item-icon-active"></slot>
    </div>
    <!-- 一般不会直接在插槽上绑定动态属性，因为渲染时会把它替换掉
     外面套一个div这样不会把原来的替换掉，上面两个最好也这样写  -->
    <div :style="activeStyle">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  data() {
    return {

    };
  },
  props:{
    path:String,
    activeColor:{
      type:String,
      default:"red"
    }
  },
  computed:{
    isActive(){
      // console.log('切换');
      return this.$route.path===this.path
    },
    activeStyle(){
      return this.isActive?{color:this.activeColor,background:'#ccc'}:{}
    }
  },
  methods: {
    itemClick(){
      this.$router.replace(this.path)
    },

  },

};
</script>

<style>
.tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}

.tab-bar-item img {
  width: 24px;
  height: 24px;
  margin-top: 3px;

  /* 去掉图片与文字默认的间隔3px */
  vertical-align: middle;

  margin-bottom: 2px;
}
</style>