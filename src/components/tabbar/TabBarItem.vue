<template>
    <div id="tab-bar-item" @click="btnClick">
        <div v-if="!isActive"> <slot name="item-icon"></slot></div>
        <div v-else><slot name="item-icon-active"></slot></div>
        <div :style="activeStyle"><slot name="item-text"></slot></div>
    </div>
</template>

<script>
export default {
    name:'TabBarItem',
    props:{
        path:String,
        activeColor:{
            type:String,
            default:"red"
        }
    },
    data() {
        return {
            // isActive:false
        }
    },
    computed:{
        isActive(){//$route是处于活跃状态的路由
            return this.$route.path == this.path
        },
        activeStyle(){
            return this.isActive ? {color:this.activeColor}:{}
        }
    },
    methods: {
        btnClick(){
            this.$router.replace(this.path).catch(err => {})
        }
    },
}
</script>

<style scoped>


#tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}
/* .active {
    color: red;
} */

#tab-bar-item img{
  width: 24px;
  height: 24px;
  margin-top: 3px;
  vertical-align: middle;
  margin-bottom: 2px;
}
</style>