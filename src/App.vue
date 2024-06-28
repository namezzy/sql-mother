<template>
  <div id="app">
    <a-row class="header" type="flex" align="middle">
      <a-col flex="160px" style="margin: 0 auto">
        <RouterLink to="/">
          <a-row align="middle">
            <img src="https://pbs.twimg.com/profile_images/1255113654049128448/J5Yt92WW_400x400.png" alt="MySQL" class="logo" />
            <span class="title">SQL训练营</span>
          </a-row>
        </RouterLink>
      </a-col>
      <a-col flex="auto">
        <a-menu
          :selected-keys="selectedKeys"
          mode="horizontal"
          :style="{ lineHeight: '64px' }"
          @click="doClickMenu"
        >
          <a-menu-item key="/learn">学习</a-menu-item>
          <a-menu-item key="/levels">关卡</a-menu-item>
          <a-menu-item key="/playground">广场</a-menu-item>
        </a-menu>
      </a-col>
    </a-row>
    <div class="content">
      <router-view />
    </div>
    <div class="footer">
      <p>
        <a-space size="middle">
         
        </a-space>
      </p>
      <p>
       
      </p>
    </div>
    <a-back-top :style="{ right: '24px' }" />
  </div>
</template>
<script setup lang="ts">
import { computed } from "vue";
import { useRoute, useRouter } from "vue-router";
import { GithubOutlined, BookOutlined } from "@ant-design/icons-vue";

const route = useRoute();
const router = useRouter();
const selectedKeys = computed(() => [route.path]);

/**
 * 点击菜单跳转
 * @param key
 */
const doClickMenu = ({ key }: any) => {
  if (key) {
    router.push({
      path: key,
    });
  }
};
</script>
<style scoped>
.header {
  border-bottom: 1px solid #f0f0f0;
  padding: 0 24px;
}

.ant-menu-horizontal {
  border-bottom: none !important;
}

.logo {
  width: 56px;
}

.title {
  margin-left: 8px;
  font-size: 20px;
  color: #000;
}

.content {
  padding: 24px;
}

.footer {
  padding: 12px;
  text-align: center;
  background: #efefef;

  p {
    margin-bottom: 4px;
  }
}
</style>
