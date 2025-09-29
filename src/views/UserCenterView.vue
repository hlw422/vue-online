<template>
  <div class="user-center">
    <el-avatar class="user_avatar" icon="el-icon-user-solid" src="http://106.14.236.60:5000/files/logo.jpg">
    </el-avatar>
    <div class="user_info">
      <el-image :src="vip_url" alt="vip标识" @click="vip_url = 'http://106.14.236.60:5000/files/VIP_shine.svg'"
        style="width: 20px; height: 20px;" />
      <div class="user_email">邮箱:</div>
      <div class="user_phone">手机号:</div>
    </div>
  </div>
  <div class="user_rank">
    <div class="user_rank_info">
      <p>排名</p>
      <p style="font-size: 20px;font-weight: bold;">1.6万</p>
      <p style="color: gray;">|</p>
      <p>积分</p>
      <p style="font-size: 20px;font-weight: bold;">8</p>
      <p style="color: gray;">|</p>
      <p>获赞</p>
      <p style="font-size: 20px;font-weight: bold;">0</p>
      <p style="color: gray;">|</p>
    </div>

    <div class="user_rank_btn">
      <el-button type="text" class="btn_edit">修改资料</el-button>
      <el-button type="text" class="btn_edit">批量导入文章</el-button>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue';

const vip_url = ref<String>('http://106.14.236.60:5000/files/VIP_gray.svg');
//const vip_url=ref<String>('http://106.14.236.60:5000/files/VIP_gray.svg');
</script>

<style scoped lang="scss">
.user-center {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: start;
  gap: 20px;
}

.user_avatar {
  width: 100px;
  height: 100px;
  line-height: 70px;
  /* 确保文字垂直居中 */
}

.user_info {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.user_rank {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
  width: 100%;
}

.user_rank_info {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.user_rank_btn {
  display: flex;
  justify-content: end;
  align-items: center;
  gap: 10px;
}
.btn_edit {
  background-color: #409eff;
  color: #fff;
  border-radius: 4px;
  padding: 5px 10px;
  font-size: 14px;
  cursor: pointer;
  width: 100px;
  font-size: 16px;
}
</style>