<template>
  <div class="home page">
    <!-- Hero 展示区 - 包含所有内容 -->
    <section class="hero">
      <!-- 主标题区域 -->
      <div class="hero-inner">
        <div class="hero-badge">全新体验</div>
        <h1 class="hero-title">
          <span class="hero-title-gradient">Vibe Coding</span>
          <br>MCP 驱动的代码风格服务器
        </h1>
        <p class="hero-subtitle">
          完全掌控、无限扩展，帮助你的开发团队快速响应变化，显著降低成本。
        </p>
        <div class="hero-actions">
          <a-button type="primary" size="large" class="hero-button-primary">下载使用</a-button>
          <a-button size="large" class="hero-button-secondary">在线体验</a-button>
        </div>
        <div class="hero-stats">
          <div class="stat-item">
            <div class="stat-number">10k+</div>
            <div class="stat-label">活跃开发者</div>
          </div>
          <div class="stat-divider"></div>
          <div class="stat-item">
            <div class="stat-number">500+</div>
            <div class="stat-label">企业用户</div>
          </div>
          <div class="stat-divider"></div>
          <div class="stat-item">
            <div class="stat-number">99.9%</div>
            <div class="stat-label">稳定性保障</div>
          </div>
        </div>
      </div>

      <!-- 核心功能区域 -->
      <div class="features-section">
        <h2 class="section-title">核心功能</h2>
        <p class="section-description">
          强大而灵活的功能集，为您的开发团队提供全方位支持
        </p>
        <div class="features-grid">
          <div class="feature-card" v-for="feature in features" :key="feature.id">
            <div class="feature-icon">
          <a-icon :name="feature.icon" :size="24" />
        </div>
            <h3 class="feature-title">{{ feature.title }}</h3>
            <p class="feature-description">{{ feature.description }}</p>
          </div>
        </div>
      </div>

      <!-- 演示视频区域 -->
      <div class="video-section">
        <h2 class="section-title">产品演示</h2>
        <div class="video-container">
          <div class="video-card">
            <div class="video-placeholder">
              <div class="play-button">
                <svg width="64" height="64" viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <circle cx="32" cy="32" r="30" fill="rgba(102, 126, 234, 0.9)"/>
                  <path d="M24 18L46 32L24 46V18Z" fill="white"/>
                </svg>
              </div>
            </div>
            <video
              controls
              poster="https://picsum.photos/seed/video-poster/1200/675"
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
      </div>

      <!-- 品牌Logo展示区 -->
      <div class="brands-section">
        <h2 class="section-title">信任我们的品牌</h2>
        <p class="brands-desc">每天都深受数百万专业开发者信赖</p>
        <div class="brands-grid">
          <div v-for="brand in brands" :key="brand.id" class="brand-logo">
            <img :src="brand.logo" :alt="brand.name" />
          </div>
        </div>
      </div>

      <!-- 成功案例区域 -->
      <div class="gallery-panel">
        <h2 class="section-title">成功案例</h2>
        <p class="section-description">
          探索我们如何帮助不同行业的客户实现开发效率的飞跃
        </p>
        <a-row :gutter="24">
          <a-col
            v-for="item in cards"
            :key="item.id"
            :xs="24"
            :sm="12"
            :md="8"
            :lg="6"
          >
            <div class="case-card">
              <div class="case-image-wrapper">
                <a-image
                  :src="item.img"
                  :alt="item.title"
                  fit="cover"
                  class="case-image"
                />
                <div class="case-overlay">
                  <div class="case-action">查看详情</div>
                </div>
              </div>
              <div class="case-content">
                <a-typography-title :heading="5" class="case-title">
                  {{ item.title }}
                </a-typography-title>
                <a-typography-paragraph type="secondary" class="case-description">
                  {{ item.desc }}
                </a-typography-paragraph>
              </div>
            </div>
          </a-col>
        </a-row>
      </div>

      <!-- 用户评价区域 -->
      <div class="testimonials-section">
        <h2 class="section-title">用户评价</h2>
        <p class="section-description">
          听听我们的用户怎么说
        </p>
        <div class="testimonials-grid">
          <div class="testimonial-card" v-for="testimonial in testimonials" :key="testimonial.id">
            <div class="testimonial-quote">{{ testimonial.quote }}</div>
            <div class="testimonial-author">
              <img :src="testimonial.avatar" alt="用户头像" class="testimonial-avatar" />
              <div class="testimonial-info">
                <div class="testimonial-name">{{ testimonial.name }}</div>
                <div class="testimonial-position">{{ testimonial.position }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- 行动号召区域 -->
      <div class="cta-section">
        <div class="cta-content">
          <h2 class="cta-title">准备好提升您的开发效率了吗？</h2>
          <p class="cta-description">
            立即加入数千家企业的行列，体验Vibe Coding带来的开发革命
          </p>
          <div class="cta-actions">
            <a-button type="primary" size="large" class="cta-button-primary">立即开始</a-button>
            <a-button size="large" class="cta-button-secondary">联系我们</a-button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts" setup>
  import { ref } from 'vue';
  import { useRouter } from 'vue-router';
  // 不需要导入图标组件，使用字符串方式

  const router = useRouter();
  const keyword = ref('');
  const onSearch = () => {
    const q = (keyword.value || '').trim();
    router.push({ name: 'search', query: { q } });
  };

  // 核心功能数据
    const features = ref([
        {
          id: 1,
          icon: 'code',
          title: '智能代码生成',
          description: '基于MCP技术的高级代码生成能力，大幅提升开发效率'
        },
        {
          id: 2,
          icon: 'zap',
          title: '极速响应',
          description: '毫秒级的API响应速度，让你的开发流程更加顺畅'
        },
        {
          id: 3,
          icon: 'shield',
          title: '企业级安全',
          description: '多层安全防护机制，保障你的代码和数据安全'
        },
        {
          id: 4,
          icon: 'users',
          title: '团队协作',
          description: '完善的团队协作功能，提升团队开发效率'
        },
        {
          id: 5,
          icon: 'layers',
          title: '无限扩展',
          description: '丰富的插件生态，满足各种开发需求'
        },
        {
          id: 6,
          icon: 'database',
          title: '云端同步',
          description: '多设备无缝同步，随时随地继续你的工作'
        }
      ]);

  // 成功案例数据
  const cards = ref(
    Array.from({ length: 8 }).map((_, i) => ({
      id: i + 1,
      title: `创新科技解决方案 ${i + 1}`,
      desc: `帮助企业客户实现数字化转型，提升开发效率300%`,
      img: `https://picsum.photos/seed/arco-${i + 1}/640/400`,
    }))
  );

  // 品牌数据
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
    }
  ]);

  // 用户评价数据
  const testimonials = ref([
    {
      id: 1,
      quote: 'Vibe Coding彻底改变了我们的开发方式，团队效率提升了300%以上！',
      name: '张小明',
      position: '某科技公司CTO',
      avatar: 'https://picsum.photos/seed/user1/100/100'
    },
    {
      id: 2,
      quote: '作为一名全栈开发者，Vibe Coding是我使用过的最强大的开发工具之一。',
      name: '李梅',
      position: '资深软件工程师',
      avatar: 'https://picsum.photos/seed/user2/100/100'
    },
    {
      id: 3,
      quote: '企业级的安全保障和无限扩展能力，让我们的开发流程更加顺畅。',
      name: '王强',
      position: '技术总监',
      avatar: 'https://picsum.photos/seed/user3/100/100'
    }
  ]);
</script>

<style scoped>
  /* 主容器 */
  .home {
    min-height: 100vh;
    position: relative;
    overflow: hidden;
  }

  /* Hero 区域 - 包含所有内容 */
  .hero {
    position: relative;
    z-index: 1;
    padding: 60px 0 100px;
  }

  .hero-inner {
    max-width: 900px;
    margin: 0 auto;
    padding: 60px 24px 60px;
    text-align: center;
  }

  .hero-badge {
    display: inline-block;
    padding: 6px 16px;
    background: rgba(102, 126, 234, 0.15);
    color: #667eea;
    border-radius: 20px;
    font-size: 14px;
    font-weight: 500;
    margin-bottom: 24px;
    backdrop-filter: blur(10px);
  }

  .hero-title {
    margin: 0 0 20px;
    font-size: 56px;
    line-height: 1.2;
    color: var(--color-text-1);
    font-weight: 700;
    letter-spacing: -0.5px;
  }

  .hero-title-gradient {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
  }

  .hero-subtitle {
    margin: 0 0 32px;
    font-size: 20px;
    color: var(--color-text-2);
    line-height: 1.6;
    max-width: 700px;
    margin-left: auto;
    margin-right: auto;
  }

  .hero-actions {
    display: inline-flex;
    gap: 16px;
    margin-bottom: 60px;
  }

  .hero-button-primary {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border: none;
    padding: 14px 32px;
    font-size: 16px;
    font-weight: 600;
    border-radius: 12px;
    box-shadow: 0 10px 30px rgba(102, 126, 234, 0.4);
    transition: all 0.3s ease;
  }

  .hero-button-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 36px rgba(102, 126, 234, 0.5);
  }

  .hero-button-secondary {
    background: rgba(255, 255, 255, 0.95);
    border: 1px solid rgba(224, 226, 236, 0.5);
    padding: 14px 32px;
    font-size: 16px;
    font-weight: 600;
    border-radius: 12px;
    color: var(--color-text-1);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
    transition: all 0.3s ease;
  }

  .hero-button-secondary:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
  }

  .hero-stats {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 32px;
    padding: 24px 0;
    border-top: 1px solid rgba(224, 226, 236, 0.3);
    border-bottom: 1px solid rgba(224, 226, 236, 0.3);
  }

  .stat-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .stat-number {
    font-size: 32px;
    font-weight: 700;
    color: var(--color-text-1);
    line-height: 1.2;
  }

  .stat-label {
    font-size: 14px;
    color: var(--color-text-3);
    margin-top: 8px;
  }

  .stat-divider {
    width: 1px;
    height: 40px;
    background: rgba(224, 226, 236, 0.3);
  }

  /* 通用区块样式 */
  .section-title {
    text-align: center;
    margin-bottom: 16px;
    font-size: 36px;
    color: var(--color-text-1);
    font-weight: 700;
    line-height: 1.3;
  }

  .section-description {
    text-align: center;
    margin-bottom: 64px;
    font-size: 16px;
    color: var(--color-text-2);
    line-height: 1.6;
    max-width: 700px;
    margin-left: auto;
    margin-right: auto;
  }

  /* 核心功能区域 */
  .features-section {
    max-width: 1200px;
    margin: 120px auto;
    padding: 0 24px;
  }

  .features-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 32px;
  }

  .feature-card {
    background: rgba(255, 255, 255, 0.8);
    border-radius: 16px;
    padding: 32px;
    text-align: center;
    backdrop-filter: blur(20px);
    border: 1px solid rgba(224, 226, 236, 0.3);
    transition: all 0.3s ease;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.05);
  }

  .feature-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 16px 48px rgba(102, 126, 234, 0.15);
  }

  .feature-icon {
    width: 80px;
    height: 80px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-radius: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 24px;
    color: white;
    box-shadow: 0 8px 24px rgba(102, 126, 234, 0.2);
  }

  .feature-title {
    font-size: 20px;
    font-weight: 600;
    color: var(--color-text-1);
    margin-bottom: 12px;
  }

  .feature-description {
    font-size: 15px;
    color: var(--color-text-2);
    line-height: 1.6;
  }

  /* 视频区域 */
  .video-section {
    max-width: 1200px;
    margin: 120px auto;
    padding: 0 24px;
  }

  .video-container {
    display: flex;
    justify-content: center;
  }

  .video-card {
    position: relative;
    width: 100%;
    max-width: 1000px;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 16px 48px rgba(0, 0, 0, 0.15);
  }

  .video-placeholder {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(0, 0, 0, 0.1);
    z-index: 1;
    cursor: pointer;
  }

  .play-button {
    transition: transform 0.3s ease;
  }

  .play-button:hover {
    transform: scale(1.1);
  }

  .demo-video {
    width: 100%;
    height: auto;
    display: block;
  }

  /* 品牌Logo区域 */
  .brands-section {
    max-width: 1200px;
    margin: 120px auto;
    padding: 0 24px;
    text-align: center;
  }

  .brands-desc {
    margin-bottom: 48px;
    color: var(--color-text-2);
    font-size: 16px;
  }

  .brands-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 48px;
    align-items: center;
    justify-items: center;
  }

  .brand-logo {
    padding: 24px;
    background: rgba(255, 255, 255, 0.8);
    border-radius: 12px;
    transition: all 0.3s ease;
    backdrop-filter: blur(10px);
    border: 1px solid rgba(224, 226, 236, 0.3);
  }

  .brand-logo:hover {
    transform: translateY(-6px);
    box-shadow: 0 12px 32px rgba(0, 0, 0, 0.1);
  }

  .brand-logo img {
    height: 48px;
    width: auto;
    max-width: 100%;
    filter: grayscale(40%);
    transition: filter 0.3s ease;
  }

  .brand-logo:hover img {
    filter: grayscale(0%);
  }

  /* 成功案例区域 */
  .gallery-panel {
    max-width: 1200px;
    margin: 120px auto;
    padding: 0 24px;
  }

  .case-card {
    background: rgba(255, 255, 255, 0.8);
    border-radius: 16px;
    overflow: hidden;
    backdrop-filter: blur(20px);
    border: 1px solid rgba(224, 226, 236, 0.3);
    transition: all 0.3s ease;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.05);
    margin-bottom: 24px;
  }

  .case-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 16px 48px rgba(0, 0, 0, 0.12);
  }

  .case-image-wrapper {
    position: relative;
    overflow: hidden;
    height: 200px;
  }

  .case-image {
    width: 100%;
    height: 100%;
    transition: transform 0.5s ease;
  }

  .case-card:hover .case-image {
    transform: scale(1.05);
  }

  .case-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(to top, rgba(0, 0, 0, 0.6), transparent);
    opacity: 0;
    transition: opacity 0.3s ease;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    padding-bottom: 20px;
  }

  .case-card:hover .case-overlay {
    opacity: 1;
  }

  .case-action {
    color: white;
    font-weight: 600;
    font-size: 16px;
  }

  .case-content {
    padding: 24px;
  }

  .case-title {
    margin: 0 0 12px !important;
    font-size: 20px;
    font-weight: 600;
    color: var(--color-text-1);
  }

  .case-description {
    margin: 0 !important;
    color: var(--color-text-2);
    line-height: 1.6;
  }

  /* 用户评价区域 */
  .testimonials-section {
    max-width: 1200px;
    margin: 120px auto;
    padding: 0 24px;
  }

  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 32px;
  }

  .testimonial-card {
    background: rgba(255, 255, 255, 0.8);
    border-radius: 16px;
    padding: 32px;
    backdrop-filter: blur(20px);
    border: 1px solid rgba(224, 226, 236, 0.3);
    transition: all 0.3s ease;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.05);
  }

  .testimonial-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 12px 36px rgba(0, 0, 0, 0.1);
  }

  .testimonial-quote {
    font-size: 16px;
    line-height: 1.8;
    color: var(--color-text-1);
    margin-bottom: 24px;
    position: relative;
  }

  .testimonial-quote::before {
    content: '"';
    font-size: 64px;
    position: absolute;
    top: -20px;
    left: -10px;
    color: rgba(102, 126, 234, 0.1);
    font-weight: 700;
  }

  .testimonial-author {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .testimonial-avatar {
    width: 48px;
    height: 48px;
    border-radius: 50%;
    object-fit: cover;
  }

  .testimonial-info {
    display: flex;
    flex-direction: column;
  }

  .testimonial-name {
    font-weight: 600;
    color: var(--color-text-1);
    font-size: 16px;
  }

  .testimonial-position {
    color: var(--color-text-3);
    font-size: 14px;
    margin-top: 4px;
  }

  /* 行动号召区域 */
  .cta-section {
    max-width: 1200px;
    margin: 120px auto 80px;
    padding: 0 24px;
  }

  .cta-content {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-radius: 24px;
    padding: 80px 40px;
    text-align: center;
    color: white;
    position: relative;
    overflow: hidden;
  }

  .cta-content::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    right: -50%;
    bottom: -50%;
    background: radial-gradient(circle, rgba(255, 255, 255, 0.15) 0%, transparent 70%);
    animation: cta-pulse 6s ease-in-out infinite;
    z-index: 0;
  }

  .cta-title {
    margin: 0 0 16px !important;
    font-size: 36px;
    font-weight: 700;
    line-height: 1.3;
    position: relative;
    z-index: 1;
  }

  .cta-description {
    margin: 0 0 32px !important;
    font-size: 18px;
    line-height: 1.6;
    max-width: 600px;
    margin-left: auto !important;
    margin-right: auto !important;
    opacity: 0.9;
    position: relative;
    z-index: 1;
  }

  .cta-actions {
    display: inline-flex;
    gap: 16px;
    position: relative;
    z-index: 1;
  }

  .cta-button-primary {
    background: white;
    color: #667eea;
    border: none;
    padding: 14px 32px;
    font-size: 16px;
    font-weight: 600;
    border-radius: 12px;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
    transition: all 0.3s ease;
  }

  .cta-button-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 36px rgba(0, 0, 0, 0.25);
  }

  .cta-button-secondary {
    background: rgba(255, 255, 255, 0.2);
    color: white;
    border: 1px solid rgba(255, 255, 255, 0.3);
    padding: 14px 32px;
    font-size: 16px;
    font-weight: 600;
    border-radius: 12px;
    backdrop-filter: blur(10px);
    transition: all 0.3s ease;
  }

  .cta-button-secondary:hover {
    transform: translateY(-3px);
    background: rgba(255, 255, 255, 0.3);
  }

  /* 渐变背景承载层 */
  .page {
    position: relative;
    min-height: 100vh;
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

  /* 动画定义 */
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

  @keyframes cta-pulse {
    0%, 100% {
      transform: scale(1);
      opacity: 0.3;
    }
    50% {
      transform: scale(1.2);
      opacity: 0.6;
    }
  }

  /* 响应式设计 */
  @media (max-width: 1024px) {
    .features-grid,
    .testimonials-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (max-width: 768px) {
    .hero {
      padding: 40px 0 80px;
    }

    .hero-inner {
      padding: 40px 20px 40px;
    }

    .hero-title {
      font-size: 36px;
    }

    .hero-subtitle {
      font-size: 16px;
    }

    .hero-actions {
      flex-direction: column;
      width: 100%;
      max-width: 300px;
      margin-left: auto;
      margin-right: auto;
    }

    .hero-stats {
      flex-direction: column;
      gap: 20px;
    }

    .stat-divider {
      width: 40px;
      height: 1px;
    }

    .section-title {
      font-size: 28px;
    }

    .features-grid,
    .testimonials-grid {
      grid-template-columns: 1fr;
    }

    .brands-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
    }

    .brand-logo {
      padding: 16px;
    }

    .brand-logo img {
      height: 36px;
    }

    .case-image-wrapper {
      height: 180px;
    }

    .cta-content {
      padding: 60px 24px;
    }

    .cta-title {
      font-size: 28px;
    }

    .cta-description {
      font-size: 16px;
    }

    .cta-actions {
      flex-direction: column;
      width: 100%;
      max-width: 300px;
      margin-left: auto;
      margin-right: auto;
    }
  }

  @media (max-width: 480px) {
    .hero-title {
      font-size: 28px;
    }

    .section-title {
      font-size: 24px;
    }

    .features-section,
    .video-section,
    .brands-section,
    .gallery-panel,
    .testimonials-section,
    .cta-section {
      margin: 80px auto;
    }

    .feature-card,
    .testimonial-card {
      padding: 24px;
    }
  }
</style>
