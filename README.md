# -封装了一个小程序的下拉框组件，因为我发现uview和uniapp都没有，使用方法示例如下

<template>
  <div>
    <dropdown :items="items" :selected="selected" @select="onSelect"></dropdown>
  </div>
</template>

<script>
import Dropdown from './Dropdown.vue';

export default {
  name: 'ParentComponent',
  components: {
    Dropdown
  },
  data() {
    return {
      items: [],
      selected: '选项1'
    };
  },
  methods: {
    onSelect(item) {
      this.selected = item;
      console.log('选中的选项是：', item);
    }
  }
};
</script>
