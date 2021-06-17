<template>
    <div id="tab-bar-item" @click="btnClick">
        <!-- <img src="../../assets/img/tabbar/home.svg" alt=""> -->
        <!-- <div>首页</div> -->
        <slot v-if="!isActive" name="item-icon"></slot>
        <slot v-else name="item-icon-active"></slot>
        <slot :class="{active: isActive}" name="item-text"></slot>
    </div>
</template>

<script>
export default {
    name:'TabBarItem',
    data() {
        return {
            isActive:false
        }
    },
    methods: {
        btnClick(){
            this.isActive = !this.isActive
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
.active {
    color: red;
}

#tab-bar-item img{
  width: 24px;
  height: 24px;
  margin-top: 3px;
  vertical-align: middle;
  margin-bottom: 2px;
}
</style>