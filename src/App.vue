<template>
  <div class="app">
    <MyHeader title="tabbar"></MyHeader>
    <component :is="componentName"></component>
    <MyFooter
      :tabList="tabList"
      @component-name="componentName = $event"
    ></MyFooter>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyFooter from './components/MyFooter.vue'

import MyGoodsList from './views/MyGoodsList.vue'
import MyGoodsSearch from './views/MyGoodsSearch.vue'
import MyUserInfo from './views/MyUserInfo.vue'
export default {
  components: {
    MyHeader,
    MyFooter,
    MyGoodsList,
    MyGoodsSearch,
    MyUserInfo
  },
  data() {
    return {
      tabList: [
        {
          iconText: 'icon-shangpinliebiao',
          text: '商品列表',
          componentName: 'MyGoodsList'
        },
        {
          iconText: 'icon-sousuo',
          text: '商品搜索',
          componentName: 'MyGoodsSearch'
        },
        {
          iconText: 'icon-user',
          text: '我的信息',
          componentName: 'MyUserInfo'
        }
      ],
      componentName: 'MyGoodsList'
    }
  }
}
</script>

<style>
.app {
  margin-top: 50px;
}
</style>
