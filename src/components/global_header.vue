<template>
  <div class="container">
    <el-row align="middle">
      <el-col :span="2">
        <div style="display: flex; align-items: center; justify-content: start;">
          <el-image class="logo" src="http://106.14.236.60:5000/files/main_logo.svg" />
          <span class="header_content_span">编程导航</span>
        </div>
      </el-col>
      <el-col :span="16">
        <el-menu mode="horizontal" ellipsis="false">
          <el-menu-item index="/home" style="font-size: 16px;">首页</el-menu-item>
          <el-menu-item index="/home" style="font-size: 16px;">交流</el-menu-item>
          <el-menu-item index="/home" style="font-size: 16px;">学习</el-menu-item>
          <el-menu-item index="/home" style="font-size: 16px;">教程</el-menu-item>
          <el-menu-item index="/home" style="font-size: 16px;">问答</el-menu-item>
          <el-menu-item index="/home" style="font-size: 16px;">问答</el-menu-item>
          <el-menu-item index="/home" style="font-size: 16px;">问答</el-menu-item>
          <el-menu-item index="/home" style="font-size: 16px;">问答</el-menu-item>
        </el-menu>
      </el-col>
      <el-col :span="4">
        <div style="display: flex; align-items: center; justify-content: end;">
          <el-button type="primary" style="margin-right: 10px;">登录</el-button>
        </div>

      </el-col>
    </el-row>
  </div>
</template>
<style scoped>
.container {
  width: 100%;
  height: 100%;
}

/* 新增：单独控制“编程导航”文本，强制不换行 + 溢出不截断（可选） */
.header_content_span {
  white-space: nowrap;
  /* 核心：禁止文本换行 */
  /* 可选：若极端窄屏，可让文本不截断（默认不设置会自然显示，无需省略号） */
  text-overflow: clip;
  overflow: visible;
}


.logo {
  flex-shrink: 0;
  /* 关键：禁止 Logo 缩小 */
  flex-grow: 0;
  /* 不允许放大 */
  min-width: 40px;
  /* 固定 Logo 宽度，确保不被挤压 */
  width: 30px;
  height: 30px;
  margin-right: 10px;
}
</style>