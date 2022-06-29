<template>
  <div>
    <button
      class="btn btn-primary btn-sm"
      style="margin-right: 5px"
      v-if="isShow"
      @click="addGoodsList = isShow = false"
    >
      +Tag
    </button>
    <input
      type="text"
      style="width: 70px"
      v-focus
      v-else
      v-model="addList"
      @blur="addTag"
      @keydown.enter="addTag"
    />
    <span
      class="badge bg-warning text-dark"
      v-for="(i, index) in tags"
      :key="index"
      style="margin-left: 5px"
      >{{ i }}</span
    >
  </div>
</template>

<script>
export default {
  props: {
    tags: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      isShow: true,
      addList: ''
    }
  },
  directives: {
    focus: {
      inserted(el) {
        el.focus()
      }
    }
  },
  methods: {
    addTag() {
      this.isShow = true
      if (this.addList.trim() !== '') {
        this.$emit('add-tag', this.addList)
      }
      this.addList = ''
    }
  }
}
</script>

<style></style>
