<template>
    <el-menu default-active="/home" class="aside-el-menu" mode="vertical" :collapse="isAsideCollapse"
        :collapse-transition="false" router active-text-color="#165dff" background-color="#f5f7fa" text-color="#333">
        <!-- 菜单1：首页 -->
        <el-menu-item index="/home">
            <el-icon>
                <HomeFilled />
            </el-icon>
            <span>首页</span>
        </el-menu-item>

        <!-- 菜单2：用户管理（含子菜单） -->
        <el-sub-menu index="/user">
            <template #title>
                <el-icon>
                    <UserFilled />
                </el-icon>
                <span>用户管理</span>
            </template>
            <el-menu-item index="/user/list">用户列表</el-menu-item>
            <el-menu-item index="/user/add">新增用户</el-menu-item>
        </el-sub-menu>

        <!-- 菜单3：系统设置 -->
        <el-menu-item index="/settings">
            <el-icon>
                <Setting />
            </el-icon>
            <span>系统设置</span>
        </el-menu-item>

        <!-- 菜单3：系统设置 -->
        <el-menu-item index="/monitor">
            <el-icon>
                <Monitor />
            </el-icon>
            <span>监控</span>
        </el-menu-item>

        <!-- 菜单4：关于我们 -->
        <el-menu-item index="/userCenter">
            <el-icon>
                <InfoFilled />
            </el-icon>
            <span>用户中心</span>
        </el-menu-item>
    </el-menu>
</template>
<script setup>

import { ref } from 'vue'
const isAsideCollapse = ref(false)
</script>