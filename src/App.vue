<template>
  <div class="common-layout">
    <el-container class="layout-container">
      <!-- 页头 -->
      <el-header class="layout-header">
        <div class="header-content">
          <span>网站标题</span>
          <!-- 页头可加折叠侧边栏的按钮 -->
          <el-button 
            icon="Menu" 
            size="small" 
            @click="isAsideCollapse = !isAsideCollapse"
            style="color: #333;"
          ></el-button>
        </div>
      </el-header>

      <!-- 中间容器：侧边栏 + 主内容 -->
      <el-container class="layout-middle">
        <!-- 侧边栏 -->
        <el-aside 
          :width="isAsideCollapse ? '64px' : '200px'"
          class="layout-aside"
        >
          <el-menu
            default-active="/home"
            class="aside-el-menu"
            mode="vertical" 
            :collapse="isAsideCollapse"
            :collapse-transition="false"
            router
            active-text-color="#165dff"
            background-color="#f5f7fa" 
            text-color="#333"
          >
            <!-- 菜单1：首页 -->
            <el-menu-item index="/home">
              <el-icon><HomeFilled /></el-icon>
              <span>首页</span>
            </el-menu-item>

            <!-- 菜单2：用户管理（含子菜单） -->
            <el-sub-menu index="/user">
              <template #title>
                <el-icon><UserFilled /></el-icon>
                <span>用户管理</span>
              </template>
              <el-menu-item index="/user/list">用户列表</el-menu-item>
              <el-menu-item index="/user/add">新增用户</el-menu-item>
            </el-sub-menu>

            <!-- 菜单3：系统设置 -->
            <el-menu-item index="/settings">
        <el-icon><Setting /></el-icon>
              <span>系统设置</span>
            </el-menu-item>

                 <!-- 菜单3：系统设置 -->
            <el-menu-item index="/monitor">
        <el-icon><Monitor /></el-icon>
              <span>监控</span>
            </el-menu-item>

            <!-- 菜单4：关于我们 -->
            <el-menu-item index="/about">
              <el-icon><InfoFilled /></el-icon>
              <span>关于我们</span>
            </el-menu-item>
          </el-menu>
        </el-aside>

        <!-- 主内容容器 -->
        <el-container class="layout-content-container">
          <el-main class="layout-main">
            <div class="main-content">
              <router-view />
            </div>
          </el-main>

          <!-- 页脚 -->
          <el-footer class="layout-footer">
            <div class="footer-content">版权信息 © 2024</div>
          </el-footer>
        </el-container>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { ElMenu, ElMenuItem, ElSubMenu, ElIcon } from 'element-plus';
import { HomeFilled, UserFilled, InfoFilled, Menu,Setting, Monitor } from '@element-plus/icons-vue';

const isAsideCollapse = ref(false);
</script>

<style scoped>
/* 基础样式 */
:root {
  --header-height: 60px;
  --footer-height: 40px;
  --aside-bg: #f5f7fa;
  --header-bg: #fff;
  --footer-bg: #f5f5f5;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body, .common-layout {
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.layout-container {
  height: 100%;
}

/* 页头 */
.layout-header {
  height: var(--header-height);
  background-color: var(--header-bg);
  color: #333;
  padding: 0 20px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.header-content {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 18px;
  font-weight: bold;
}

/* 中间容器 */
.layout-middle {
  height: calc(100% - var(--header-height));
  display: flex;
}

/* 侧边栏 */
.layout-aside {
  background-color: var(--aside-bg);
  box-shadow: 2px 0 8px rgba(0, 0, 0, 0.05);
  transition: width 0.3s ease;
}

/* el-menu 样式 */
.aside-el-menu {
  border-right: none;
  height: 100%;
}
.layout-footer{
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  text-align: center;
}
</style>