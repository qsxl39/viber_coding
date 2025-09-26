<template>
  <div class="home page">
    <!-- 顶部简易导航，右上角“登录” -->
    <div class="topbar">
      <div class="logo">Vibe Coding</div>
      <div class="actions">
        <router-link to="/login">
          <a-button type="primary" size="small">登录</a-button>
        </router-link>
      </div>
    </div>

    <!-- Hero 展示区 -->
    <section class="hero">
      <div class="hero-inner">
        <h1 class="hero-title">MCP 驱动的代码风格服务器</h1>
        <p class="hero-subtitle">
          Vibe
          Coding--完全掌控、无限扩展，帮助你的开发团队快速响应变化，显著降低成本。
        </p>
        <div class="hero-actions">
          <a-button type="primary" size="large">适合你吗？</a-button>
          <a-button size="large" style="margin-left: 12px">在线体验</a-button>
        </div>
      </div>
    </section>

    <!-- 图片卡片列表：整体大圆角容器 -->
    <section class="gallery-panel">
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
      title: `测试案例 ${i + 1}`,
      desc: `模板生成的网站${i + 1}`,
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
    z-index: 1;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 66px;
    padding: 0 20px;
    background: linear-gradient(
      90deg,
      rgba(93, 135, 255, 0.2) 0%,
      rgba(57, 197, 187, 0.2) 100%,
      rgba(255, 102, 102, 0.18) 50%
    );
    -webkit-backdrop-filter: saturate(180%) blur(10px);
    backdrop-filter: saturate(180%) blur(10px);
    border-bottom: 1px solid rgba(0, 0, 0, 0.06);
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.04);
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
    position: relative;
    overflow: hidden;
    z-index: 1;
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
  .gallery-panel {
    margin: 24px auto;
    padding: 20px;
    max-width: 1220px;
    border-radius: 18px;
    background: white;
    border: 1px solid var(--color-border);
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.06);
    position: relative;
    z-index: 1;
  }

  /* 页面统一的渐变背景（Hero 与列表共用） */
  .page {
    position: relative;
    overflow: hidden;
  }
  .page::before {
    content: '';
    position: absolute;
    inset: -20%;
    background: radial-gradient(
        60% 80% at 20% 20%,
        rgba(93, 135, 255, 0.35),
        transparent 60%
      ),
      radial-gradient(
        60% 80% at 80% 30%,
        rgba(57, 197, 187, 0.35),
        transparent 60%
      ),
      radial-gradient(
        70% 90% at 50% 80%,
        rgba(255, 102, 102, 0.28),
        transparent 60%
      );
    filter: blur(40px) saturate(120%);
    transform: translate3d(0, 0, 0);
    animation: hero-flow 14s ease-in-out infinite alternate;
    pointer-events: none;
    z-index: 0;
  }

  /* 顶部提亮椭圆：最底层的半透明白色模糊区域 */
  .page::after {
    content: '';
    position: absolute;
    left: 50%;
    top: 8vh;
    width: 65vw;
    height: 36vh;
    transform: translateX(-50%);
    border-radius: 50% / 45%;
    background: radial-gradient(
      ellipse at center,
      rgba(255, 255, 255, 0.55),
      rgba(255, 255, 255, 0) 70%
    );
    filter: blur(28px);
    pointer-events: none;
    z-index: 0; /* 与 ::before 同层，仍在内容层之下 */
  }

  @keyframes hero-flow {
    0% {
      transform: translate3d(-2%, -2%, 0) scale(1.05) rotate(0deg);
    }
    50% {
      transform: translate3d(2%, 1%, 0) scale(1.08) rotate(8deg);
    }
    100% {
      transform: translate3d(-1%, 3%, 0) scale(1.03) rotate(-6deg);
    }
  }
</style>
