<template>
  <el-card class="cpu-monitor-card" hoverable :style="{ maxWidth: '480px' }">
    <!-- 卡片头部：标题 + 状态标识 -->
    <template #header>
      <div class="card-header">
        <div class="header-left">
          <el-icon class="header-icon">
            <Cpu />
          </el-icon>
          <span class="header-title">CPU 占用率监控</span>
        </div>
        <!-- 状态标签：根据使用率动态切换颜色 -->
        <el-tag :type="cpuUsage > 80 ? 'danger' : cpuUsage > 50 ? 'warning' : 'success'" size="small">
          {{ cpuUsage > 80 ? '高负载' : cpuUsage > 50 ? '中负载' : '低负载' }}
        </el-tag>
      </div>
    </template>

    <!-- 卡片主体：使用率数字 + 进度条可视化 -->
    <div class="card-body">
      <!-- 使用率大数字 -->
      <div class="usage-number">
        <span class="number" :class="{ high: cpuUsage > 80, medium: cpuUsage > 50 }">
          {{ cpuUsage.toFixed(1) }}%
        </span>
        <!-- 动态加载动画（模拟数据刷新） -->
        <el-skeleton :loading="isRefreshing" active class="refresh-skeleton">
          <span></span>
        </el-skeleton>
      </div>

      <!-- 进度条：直观展示使用率 -->
      <el-progress :percentage="cpuUsage" :stroke-width="8"
        :status="cpuUsage > 80 ? 'exception' : cpuUsage > 50 ? 'warning' : 'success'" class="usage-progress" />

      <!-- 补充信息：核心数 + 最近负载 -->
      <div class="usage-meta">
        <span class="meta-item">
          <el-icon size="14">
            <Microchip />
          </el-icon>
          8核 (4物理 + 4逻辑)
        </span>
        <span class="meta-item">
          <el-icon size="14">
            <Timer />
          </el-icon>
          15分钟负载: {{ loadAverage.toFixed(2) }}
        </span>
      </div>
    </div>

    <!-- 卡片底部：更新时间 + 刷新按钮 -->
    <template #footer>
      <div class="card-footer">
        <span class="update-time">
          最后更新: {{ currentTime }}
        </span>
        <el-button icon="refresh" size="mini" circle @click="refreshData" :loading="isRefreshing" class="refresh-btn" ></el-button>
      </div>
    </template>
  </el-card>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { Cpu, Timer, Refresh } from '@element-plus/icons-vue';
import { ElTag, ElProgress, ElSkeleton, ElButton, ElIcon } from 'element-plus';

// 核心数据
const cpuUsage = ref(80.0); // CPU使用率
const loadAverage = ref(1.23); // 15分钟负载
const currentTime = ref(new Date().toLocaleString()); // 更新时间
const isRefreshing = ref(false); // 刷新状态

// 模拟数据刷新
const refreshData = () => {
   console.log('App.vue mounted',cpuUsage);
  isRefreshing.value = true;
  // 模拟接口请求延迟
  setTimeout(() => {
    // 随机生成50-90之间的使用率（模拟波动）
    cpuUsage.value = Math.random() * 40 + 50;
    // 随机生成0.8-2.0之间的负载
    loadAverage.value = Math.random() * 1.2 + 0.8;
    // 更新时间
    currentTime.value = new Date().toLocaleString();
    isRefreshing.value = false;
  }, 800);
};

// 页面挂载后自动刷新一次
onMounted(() => {
  refreshData();
});
</script>

<style scoped lang="scss">
.cpu-monitor-card {
  border-radius: 12px !important;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08) !important;
  transition: all 0.3s ease;

  &:hover {
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12) !important;
  }
}

// 头部样式
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 !important;

  .header-left {
    display: flex;
    align-items: center;
    gap: 8px;

    .header-icon {
      color: #165dff;
      font-size: 18px;
    }

    .header-title {
      font-size: 16px;
      font-weight: 600;
      color: #333;
    }
  }
}

// 主体样式
.card-body {
  padding: 20px 15px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

// 使用率数字
.usage-number {
  display: flex;
  align-items: baseline;
  gap: 12px;
  min-height: 56px;

  .number {
    font-size: 48px;
    font-weight: 700;
    color: #333;
    line-height: 1;
    transition: color 0.3s ease;

    &.high {
      color: #ff4d4f; // 高负载红色
    }

    &.medium {
      color: #faad14; // 中负载黄色
    }
  }

  .refresh-skeleton {
    width: 24px;
    height: 24px;
    margin-top: 6px;
  }
}

// 进度条
.usage-progress {
  width: 100%;
  margin-top: 8px;
  clear: both;
}

// 补充元信息
.usage-meta {
  display: flex;
  gap: 16px;
  margin-top: 4px;

  .meta-item {
    display: flex;
    align-items: center;
    gap: 4px;
    font-size: 12px;
    color: #666;

    :deep(.el-icon) {
      color: #999;
    }
  }
}

// 底部样式
.card-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 15px !important;
  border-top: 1px solid #f5f5f5;

  .update-time {
    font-size: 12px;
    color: #999;
  }

  .refresh-btn {
    width: 30px;
    height: 30px;
    padding: 0;
    background-color: transparent;
    transition: color 0.2s;

    &:hover {
      color: #165dff;
    }

    &:loading {
      color: #165dff;
    }
  }
}
</style>