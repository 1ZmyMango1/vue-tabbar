<template>
  <div>
    商品列表
    <MyTable :goodsList="goodsList">
      <template #hear>
        <th>#</th>
        <th>商品名称</th>
        <th>价格</th>
        <th>标签</th>
        <th>操作</th>
      </template>

      <template #body="{ item }">
        <td>{{ item.id }}</td>
        <td>{{ item.goods_name }}</td>
        <td>{{ item.goods_price }}</td>
        <td>
          <AddTags :tags="item.tags" @add-tag="addTag(item, $event)"></AddTags>
        </td>
        <td>
          <button class="btn btn-danger btn-sm" @click="delGoodsList(item.id)">
            删除
          </button>
        </td>
      </template>
    </MyTable>
  </div>
</template>

<script>
import MyTable from '../components/MyTable.vue'
import AddTags from '../components/AddTags.vue'
import axios from '../utils/request.js'
export default {
  components: {
    MyTable,
    AddTags
  },
  data() {
    return {
      goodsList: []
    }
  },
  created() {
    this.getGoods()
  },
  methods: {
    async getGoods() {
      const { data } = await axios({
        url: '/api/goods'
      })
      this.goodsList = data.data
      console.log(data)
    },
    delGoodsList(id) {
      this.goodsList = this.goodsList.filter((item) => item.id !== id)
    },
    addTag(item, addList) {
      console.log(item)
      console.log(addList)
      item.tags.push(addList)
    }
  }
}
</script>

<style></style>
