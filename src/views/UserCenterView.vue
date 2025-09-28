<template>
  <div class="user-center">
    <div style="height:px;background-color: white;margin: 50px;">
      <el-avatar src="http://106.14.236.60:5000/files/logo.jpg" style="width: 150px;height: 150px;">
      </el-avatar>
    </div>
    <div class="items">
      <div class="item">
        <div class="vipLevel">
          <div>
            <img :src="currentVipUrl" style="width: 30px;height: 30px;" alt="">
          </div>
        </div>
      </div>
      <div class="item" warp>暂无简介</div>
      <div class="item">女</div>
    </div>
    <el-button type="primary" style="margin-top: 20px;" @click="handleEditVip">修改VIP信息</el-button>
  </div>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'
const vip_url_shine = ref<String>("http://106.14.236.60:5000/files/VIP_shine.svg");
const vip_url_gray = ref<String>("http://106.14.236.60:5000/files/VIP_gray.svg");

// 正确定义计算属性：返回当前应该显示的VIP图片地址
const currentVipUrl = computed(() => {
  console.log("computed 被调用", is_vip.value);
  return is_vip.value ? vip_url_shine.value : vip_url_gray.value;
})
const is_vip = ref<Boolean>(false);

const handleEditVip = () => {
  is_vip.value = !is_vip.value;
}
</script>
<style scoped>
.user-center {
  display: flex;
  justify-content: start;
  align-items: center;
}

.vipLevel {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
}

.items {
  display: flex;
  flex-direction: column;
  justify-content: space-between
}

.item {
  height: 30px;
  margin: 10px;
}
</style>