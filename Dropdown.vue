<template>
  <view class="dropdown">
	  <view style="display:flex;justify-content: space-between;align-items:center;padding: 0 20rpx;" @tap="toggleDropdown">
         <view class="selected-item" >{{ selected }}</view>
		 <image style="width:44rpx;height: 44rpx;" src="../static/img/组 35165@2x.png"></image>
	  </view>
	  
      <scroll-view class="dropdown-menu" :style="{ display: isOpen ? 'block' : 'none' }" scroll-y="true">
        <view v-for="(item, index) in items" :key="index" @tap="selectItem(item)">{{ item.label}}</view>
      </scroll-view>
  </view>
</template>

<script>
export default {
  name: 'Dropdown',
  props: {
    items: {
      type: Array,
      required: true
    },
    selected: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      isOpen: false
    };
  },
  methods: {
    toggleDropdown() {
      this.isOpen = !this.isOpen;
    },
    selectItem(item) {
      this.$emit('select', item);
      this.isOpen = false;
    }
  }
};
</script>

<style>
.dropdown {
  position: relative;
  display: inline-block;
  width: 240rpx;
  height: 60rpx;
  line-height: 60rpx;
  background: #FFF;
  border-radius: 10rpx 10rpx 10rpx 10rpx;
  opacity: 1;
  border: 2rpx solid #C8D1DB;
  
}

.selected-item {
  cursor: pointer;
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1;
  display: none;
  margin: 0;
  padding: 0;
  min-height: 60rpx;
  max-height: 300rpx;
  list-style: none;
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  width: 240rpx;
  background:#fff;
  border-radius: 10rpx 10rpx 10rpx 10rpx;
  opacity: 1;
  border: 2rpx solid #C8D1DB;
  text-align: center;
}

.dropdown-menu view {
  padding: 20rpx;
  cursor: pointer;
}

.dropdown-menu view:hover {
  background-color: #f2f2f2;
}
</style>
