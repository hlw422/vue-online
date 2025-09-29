<script setup lang="ts">
import Global_header from '@/components/global_header.vue';
import Global_footer from '@/components/global_footer.vue';
import Global_main from '@/components/global_main.vue';

</script>

<template>
  <el-container>
    <el-header>
      <Global_header/>
    </el-header>
        <el-main>
          <Global_main/>
        </el-main>
    <el-footer>
      <Global_footer/> 
    </el-footer>
  </el-container>
</template>


<style lang="scss" scoped>
</style>