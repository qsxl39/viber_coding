<template>
  <div class="home page">
    <!-- 顶部简易导航，右上角"登录" -->
    <div class="topbar">
      <div class="left">
        <div class="logo">Vibe Coding</div>
      </div>
      <div class="center">
        <a-link class="nav-item" @click="$router.push('/explore')">探索</a-link>
        <a-link class="nav-item" @click="$router.push('/catalog')">目录</a-link>
        <a-input-search
          v-model="keyword"
          allow-clear
          placeholder="搜索代码风格、规范等..."
          :style="{ width: '720px', maxWidth: '65vw' }"
          class="rounded-search"
          @search="onSearch"
        />
        <a-link class="nav-item" @click="$router.push('/login')">登录</a-link>
        <a-link class="nav-item" @click="$router.push('/register')"
          >注册</a-link
        >
      </div>
      <div class="right">
        <a-button type="primary" size="small" @click="$router.push('/submit')"
          >提交灵感</a-button
        >
      </div>
    </div>

    <!-- Hero 展示区 - 包含所有内容 -->
    <section class="hero">
      <!-- 主标题区域 -->
      <div class="hero-inner">
        <h1 class="hero-title">MCP 驱动的代码风格服务器</h1>
        <p class="hero-subtitle">
          Vibe
          Coding--完全掌控、无限扩展，帮助你的开发团队快速响应变化，显著降低成本。
        </p>
        <div class="hero-actions">
          <a-button type="primary" size="large">下载使用</a-button>
          <a-button size="large" style="margin-left: 12px">在线体验</a-button>
        </div>
      </div>

      <!-- 演示视频区域 -->
      <div class="video-section">
        <h2 class="section-title">产品演示</h2>
        <div class="video-container">
          <video
            controls
            poster="https://picsum.photos/seed/video-poster/800/450"
            class="demo-video"
          >
            <!-- 视频URL占位1 -->
            <source src="YOUR_VIDEO_URL_1" type="video/mp4" />
            <!-- 视频URL占位2 -->
            <source src="YOUR_VIDEO_URL_2" type="video/webm" />
            <!-- 视频URL占位3 -->
            <source src="YOUR_VIDEO_URL_3" type="video/ogg" />
            您的浏览器不支持视频播放。
          </video>
        </div>
      </div>

      <!-- 品牌Logo展示区 -->
      <div class="brands-section">
        <h2 class="section-title">信任我们的品牌</h2>
        <p class="brands-desc">每天都深受数百万专业开发者信赖。</p>
        <div class="brands-grid">
          <div v-for="brand in brands" :key="brand.id" class="brand-logo">
            <img :src="brand.logo" :alt="brand.name" />
          </div>
        </div>
      </div>

      <!-- 图片卡片列表 -->
      <div class="gallery-panel">
        <h2 class="section-title">成功案例</h2>
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
      </div>
    </section>
  </div>
</template>

<script lang="ts" setup>
  import { ref } from 'vue';
  import { useRouter } from 'vue-router';

  const router = useRouter();
  const keyword = ref('');
  const onSearch = () => {
    const q = (keyword.value || '').trim();
    router.push({ name: 'search', query: { q } });
  };

  const cards = ref(
    Array.from({ length: 12 }).map((_, i) => ({
      id: i + 1,
      title: `测试案例 ${i + 1}`,
      desc: `模板生成的网站${i + 1}`,
      img: `https://picsum.photos/seed/arco-${i + 1}/640/360`,
    }))
  );

  const brands = ref([
    {
      id: 1,
      name: 'TechCorp',
      logo: 'https://pic1.imgdb.cn/item/68f4ed153203f7be007e64cd.svg',
    },
    {
      id: 2,
      name: 'InnovateLab',
      logo: 'https://pic1.imgdb.cn/item/68f4ed153203f7be007e64cd.svg',
    },
    {
      id: 3,
      name: 'DevStudio',
      logo: 'https://pic1.imgdb.cn/item/68f4ed153203f7be007e64cd.svg',
    },
    {
      id: 4,
      name: 'CodeWorks',
      logo: 'https://pic1.imgdb.cn/item/68f4ed153203f7be007e64cd.svg',
    },
    {
      id: 5,
      name: 'FutureTech',
      logo: 'https://pic1.imgdb.cn/item/68f4ed153203f7be007e64cd.svg',
    },
    {
      id: 6,
      name: 'SmartDev',
      logo: 'https://pic1.imgdb.cn/item/68f4ed153203f7be007e64cd.svg',
    },
    {
      id: 7,
      name: 'SmartDev',
      logo: 'https://pic1.imgdb.cn/item/68f4ed153203f7be007e64cd.svg',
    },
  ]);
</script>

<style scoped>
  /* 全局页面高度修正 */
  html,
  body {
    width: 100%;
    height: 100%;
    min-width: 10000px;
    margin: 0;
    padding: 0;
    background: transparent; /* 不干扰.page背景 */
    background: none !important; /* ✅ 去掉 Arco 自带的渐变背景 */
  }
  /* 主容器 */
  .home {
    min-height: 100vh;
    position: relative;
    overflow: hidden;
  }
  .topbar {
    position: sticky;
    top: 0;
    z-index: 1;
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    height: 66px;
    padding: 0 20px;
    background-color: rgba(255, 255, 255, 0.4);
    -webkit-backdrop-filter: saturate(180%) blur(10px);
    backdrop-filter: saturate(180%) blur(10px);
    border-bottom: 1px solid rgba(0, 0, 0, 0.06);
  }
  .left {
    display: flex;
    align-items: center;
    gap: 16px;
  }
  .logo {
    font-weight: 600;
  }
  .center {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
  }
  .right {
    display: flex;
    justify-content: flex-end;
    gap: 8px;
    align-items: center;
  }

  /* 四个导航项：朴素样式、黑色文字、稍大字号、无夸张悬停 */
  .nav-item,
  .nav-item:visited {
    color: #000000b6 !important;
    font-size: 16px;
    font-weight: 320;
    padding: 4px 8px; /* 为阴影和浮起预留可点击区域 */
    border-radius: 8px; /* 柔和圆角但无背景 */
    transition: color 0.25s ease, transform 0.48s ease, box-shadow 0.2s ease;
  }
  .nav-item:hover {
    color: #111 !important;
    opacity: 1;
    text-decoration: none;
    transform: translateY(-2px);
    box-shadow: 0 6px 18px rgba(255, 255, 255, 0.45);
  }

  /* 顶部搜索框通用圆角（无需额外类名） */
  /* .topbar :deep(.arco-input-search .arco-input-group) {
    border-radius: 4px;
    overflow: hidden;
  } */

  /* 直接作用于 Arco 的搜索外层 wrapper，确保覆盖默认半径 */
  .topbar :deep(.arco-input-wrapper.arco-input-search) {
    --border-radius-small: 24px; /* 覆盖内部使用的变量 */
    border-radius: 8px !important;
    overflow: hidden;
    background: linear-gradient(
      135deg,
      #8fa8d9 0%,
      #9a8fd8 25%,
      #88c9c2 50%,
      #6db5e6 75%,
      #8cb4e8 100%
    );
    background-size: 400% 400% !important;
    animation: gradientShift 8s ease infinite;
    /* backdrop-filter: blur(100px); */
    border: none;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  /* 去掉输入框/前后缀的竖线与边框以及光标 */
  .topbar :deep(.arco-input-wrapper.arco-input-search .arco-input) {
    border: none !important;
    box-shadow: none !important;
    caret-color: transparent; /* 隐藏黑色输入光标 */
  }
  .topbar :deep(.arco-input-prefix),
  .topbar :deep(.arco-input-suffix),
  .topbar :deep(.arco-input-group-addafter),
  .topbar :deep(.arco-input-group-addbefore) {
    border: none !important;
  }

  @keyframes gradientShift {
    0% {
      background-position: 0% 0%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 100%;
    }
  }

  /* 搜索框圆角 */
  /* :deep(.rounded-search .arco-input-group) {
    border-radius: 24px;
    overflow: hidden;
  } */

  /* Hero 区域 - 包含所有内容 */
  .hero {
    position: relative;
    z-index: 1;
    padding: 40px 0;
  }

  .hero-inner {
    max-width: 900px;
    margin: 0 auto;
    padding: 60px 24px 40px;
    text-align: center;
  }
  .hero-title {
    margin: 0 0 12px;
    font-size: 44px;
    line-height: 1.2;
    color: var(--color-text-1);
  }
  .hero-subtitle {
    margin: 0 0 20px;
    font-size: 16px;
    color: var(--color-text-2);
    line-height: 1.6;
  }
  .hero-actions {
    display: inline-flex;
  }

  /* 通用区块样式 */
  .section-title {
    text-align: center;
    margin-bottom: 32px;
    font-size: 28px;
    color: var(--color-text-1);
    font-weight: 600;
  }

  /* 视频区域 */
  .video-section {
    max-width: 900px;
    margin: 60px auto;
    padding: 0 24px;
  }

  .video-container {
    display: flex;
    justify-content: center;
  }

  .demo-video {
    width: 100%;
    min-width: 1200px;
    height: auto;
    border-radius: 12px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.15);
  }

  /* 品牌Logo区域 */
  .brands-section {
    max-width: 1000px;
    margin: 70px auto;
    padding: 0 24px;
    text-align: center; /* 新增，使描述文字和logo居中 */
  }

  .brands-desc {
    margin-bottom: 32px; /* 新增，与logo区域拉开距离 */
    color: var(--color-text-2);
  }
  .brands-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(90px, 1fr)); /* 调整列宽 */
    gap: 40px;
    align-items: center;
    justify-items: center;
  }

  .brand-logo {
    padding: 16px;
    background: rgba(255, 255, 255, 0.35); /* 卡片半透明 */
    border-radius: 4px;
    transition: all 0.3s ease;
  }

  .brand-logo:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
  }

  .brand-logo img {
    height: 40px; /* 调整logo高度 */
    width: 48px;
    filter: grayscale(30%);
    transition: filter 0.3s ease;
  }

  .brand-logo:hover img {
    filter: grayscale(0%);
  }

  /* 图片卡片列表 */
  .gallery-panel {
    max-width: 1220px;
    margin: 60px auto 40px;
    padding: 40px 20px;
  }

  /* 渐变背景承载层 */
  .page {
    position: relative;
    min-height: 100vh; /* ✅ 确保背景至少覆盖整屏 */
    width: 100%;
    overflow: hidden;
    display: flex;
    flex-direction: column;
  }

  /* 背景动画部分 */
  .page::before {
    content: '';
    position: absolute;
    inset: -20%;
    background: radial-gradient(
        60% 80% at 20% 20%,
        rgba(143, 168, 217, 0.35),
        transparent 60%
      ),
      radial-gradient(
        60% 80% at 80% 30%,
        rgba(154, 143, 216, 0.35),
        transparent 60%
      ),
      radial-gradient(
        70% 90% at 50% 80%,
        rgba(136, 201, 194, 0.4),
        transparent 60%
      ),
      radial-gradient(
        60% 80% at 30% 70%,
        rgba(109, 181, 230, 0.3),
        transparent 60%
      ),
      radial-gradient(
        60% 80% at 70% 20%,
        rgba(140, 180, 232, 0.25),
        transparent 60%
      );
    filter: blur(40px) saturate(120%);
    animation: hero-flow 14s ease-in-out infinite alternate;
    pointer-events: none;
    z-index: 0;
  }

  /* 顶部提亮椭圆 */
  .page::after {
    content: '';
    position: absolute;
    left: 50%;
    top: 8vh;
    width: 105vw;
    height: 36vh;
    transform: translateX(-50%);
    border-radius: 50% / 45%;
    background: radial-gradient(
      ellipse at center,
      rgba(255, 255, 255, 0.75),
      rgba(255, 255, 255, 0) 60%
    );
    filter: blur(30px);
    pointer-events: none;
    z-index: 0;
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

  /* 响应式设计 */
  @media (max-width: 768px) {
    .hero-inner {
      padding: 40px 20px 20px;
    }

    .hero-title {
      font-size: 32px;
    }

    .section-title {
      font-size: 24px;
    }

    .brands-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
    }

    .brand-logo {
      padding: 15px;
    }

    .brand-logo img {
      height: 30px;
    }
  }
</style>
