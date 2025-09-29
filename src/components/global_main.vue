<template>
    <el-container class="layout-middle">
        <!-- 侧边栏 -->
        <el-aside :width="isAsideCollapse ? '64px' : '200px'" class="layout-aside">
           <Global_menu/>
            </el-aside>
        <!-- 内容 -->
        <el-main class="layout-main">
            <router-view></router-view>
        </el-main>
    </el-container>
</template>
<script setup lang="ts">
import { ref } from 'vue'
import Global_menu from './global_menu.vue'
const isAsideCollapse = ref(false)
</script>