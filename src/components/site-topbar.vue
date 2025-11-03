<template>
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
      <a-link class="nav-item" @click="$router.push('/register')">注册</a-link>
    </div>
    <div class="right">
      <a-button type="primary" size="small" @click="$router.push('/submit')"
        >上传模板</a-button
      >
    </div>
  </div>
</template>

<script setup lang="ts">
  import { ref } from 'vue';
  import { useRouter } from 'vue-router';

  const router = useRouter();
  const keyword = ref('');
  const onSearch = () => {
    const q = (keyword.value || '').trim();
    router.push({ name: 'search', query: { q } });
  };
</script>

<style scoped>
  .topbar {
    position: sticky;
    top: 0;
    z-index: 10;
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

  .nav-item,
  .nav-item:visited {
    color: #000000b6 !important;
    font-size: 16px;
    font-weight: 320;
    padding: 4px 8px;
    border-radius: 8px;
    transition: color 0.25s ease, transform 0.48s ease, box-shadow 0.2s ease;
  }
  .nav-item:hover {
    color: #111 !important;
    opacity: 1;
    text-decoration: none;
    transform: translateY(-2px);
    box-shadow: 0 6px 18px rgba(255, 255, 255, 0.45);
  }

  /* 搜索框外层样式与圆角 */
  :deep(.arco-input-wrapper.arco-input-search) {
    --border-radius-small: 24px;
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
    border: none;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
  /* 去掉输入框/前后缀的竖线与边框以及光标 */
  :deep(.arco-input-wrapper.arco-input-search .arco-input) {
    border: none !important;
    box-shadow: none !important;
    caret-color: transparent;
  }
  :deep(.arco-input-prefix),
  :deep(.arco-input-suffix),
  :deep(.arco-input-group-addafter),
  :deep(.arco-input-group-addbefore) {
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
</style>
