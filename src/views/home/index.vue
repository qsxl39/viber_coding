<template>
  <div class="home">
    <!-- 顶部简易导航，右上角“登录” -->
    <div class="topbar">
      <div class="logo">NoCode</div>
      <div class="actions">
        <router-link to="/login">
          <a-button type="primary" size="small">登录</a-button>
        </router-link>
      </div>
    </div>

    <!-- Hero 展示区 -->
    <section class="hero">
      <div class="hero-inner">
        <h1 class="hero-title">极易扩展的无代码开发平台</h1>
        <p class="hero-subtitle">
          完全掌控、无限扩展，帮助你的开发团队快速响应变化，显著降低成本。
        </p>
        <div class="hero-actions">
          <a-button type="primary" size="large">适合你吗？</a-button>
          <a-button size="large" style="margin-left: 12px">在线体验</a-button>
        </div>
      </div>
    </section>

    <!-- 图片卡片列表 -->
    <section class="gallery">
      <a-row :gutter="16">
        <a-col
          v-for="item in cards"
          :key="item.id"
          :xs="24"
          :sm="12"
          :md="8"
          :lg="6"
        >
          <a-card :hoverable="true" :style="{ marginBottom: '16px' }">
            <template #cover>
              <a-image
                :src="item.img"
                :alt="item.title"
                fit="cover"
                height="160"
              />
            </template>
            <a-typography-title :heading="6" :style="{ margin: '8px 0 4px' }">
              {{ item.title }}
            </a-typography-title>
            <a-typography-paragraph type="secondary" :style="{ margin: 0 }">
              {{ item.desc }}
            </a-typography-paragraph>
          </a-card>
        </a-col>
      </a-row>
    </section>
  </div>
</template>

<script lang="ts" setup>
  import { ref } from 'vue';

  const cards = ref(
    Array.from({ length: 12 }).map((_, i) => ({
      id: i + 1,
      title: `精选案例 ${i + 1}`,
      desc: '低门槛搭建业务应用的示例',
      img: `https://picsum.photos/seed/arco-${i + 1}/640/360`,
    }))
  );
</script>

<style scoped>
  .home {
    min-height: 100vh;
  }
  .topbar {
    position: sticky;
    top: 0;
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 56px;
    padding: 0 20px;
    background: var(--color-bg-2);
    border-bottom: 1px solid var(--color-border);
  }
  .logo {
    font-weight: 600;
  }
  .actions {
    display: flex;
    align-items: center;
  }
  .hero {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 56vh;
    text-align: center;
    background: linear-gradient(180deg, var(--color-bg-2), transparent);
  }
  .hero-inner {
    max-width: 900px;
    padding: 0 24px;
  }
  .hero-title {
    margin: 0 0 12px;
    font-size: 44px;
    line-height: 1.2;
  }
  .hero-subtitle {
    margin: 0 0 20px;
    font-size: 16px;
    color: var(--color-text-2);
  }
  .hero-actions {
    display: inline-flex;
  }
  .gallery {
    padding: 20px;
  }
</style>
