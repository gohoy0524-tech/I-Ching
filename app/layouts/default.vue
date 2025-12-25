<script setup lang="ts">
import type { NavigationMenuItem } from "@nuxt/ui";

const items: NavigationMenuItem[] = [
  {
    label: "I-CHING",
    to: "/",
    active: true,
  },
  {
    label: "CTM(Chinese Traditional Medicine)",
    to: "/ctm",
  },
  {
    label: "J-POP",
    to: "/j-pop",
  },
];

// 控制侧边栏折叠状态
const sidebarCollapsed = ref(false);
</script>

<template>
  <!-- 1. UDashboardGroup: 最外层容器，管理侧边栏状态和持久化 -->
  <UDashboardGroup>
    <!-- 2. UDashboardSidebar: 侧边栏组件 -->
    <UDashboardSidebar v-model:collapsed="sidebarCollapsed" collapsible>
      <!-- Header 插槽: 侧边栏头部 -->
      <template #header="{ collapsed, collapse }">
        <UButton
          :icon="collapsed ? 'i-lucide-menu' : 'i-lucide-menu'"
          variant="ghost"
          color="neutral"
          @click="collapse?.(!collapsed)"
        />
      </template>
      <!-- Default 插槽: 侧边栏主体内容 -->
      <template #default="{ collapsed }">
        <!-- 导航菜单组 1 -->
        <UNavigationMenu
          :collapsed="collapsed"
          :items="items"
          orientation="vertical"
        >
          <template #item-label="{ item }">
            <span class="text-2xl font-stretch-expanded">{{ item.label }}</span>
          </template>
        </UNavigationMenu>
      </template>
    </UDashboardSidebar>

    <!-- 3. UDashboardPanel: 主内容面板 -->
    <UDashboardPanel>
      <!-- Header 插槽: 顶部导航栏 -->
      <template #header>
        <UDashboardNavbar title="Gohoy's interests">
          <template #right>
            <!-- 右侧操作按钮 -->
            <UButton icon="i-lucide-bell" color="neutral" variant="ghost" />
            <UButton icon="i-lucide-settings" color="neutral" variant="ghost" />
          </template>
        </UDashboardNavbar>
      </template>

      <!-- Body 插槽: 页面主要内容 -->
      <template #body>
        <slot />
      </template>
    </UDashboardPanel>
  </UDashboardGroup>
</template>
