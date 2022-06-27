<template>
  <div class="my-tab-bar">
    <div
      class="tab-item"
      :class="{ current: currentIndex === index }"
      v-for="(item, index) in tabList"
      :key="index"
      @click="btnCurrent(index, item.componentName)"
    >
      <!-- 图标 -->
      <span :class="`iconfont ${item.iconText}`" id="app"></span>
      <!-- 文字 -->
      <span>{{ item.text }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tabList: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      currentIndex: 0,
      componentName: ''
    }
  },
  methods: {
    btnCurrent(index, comName) {
      this.currentIndex = index
      this.componentName = comName
      this.$emit('component-name', this.componentName)
    }
  }
}
</script>

<style lang="less" scoped>
.my-tab-bar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: white;
  .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

.current {
  color: #1d7bff;
  .iconfont {
    color: #1d7bff;
  }
}

#app {
  margin: -8px;
}
</style>
