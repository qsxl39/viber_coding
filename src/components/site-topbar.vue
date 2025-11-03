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
      <a-link class="nav-item" @click.prevent="openAuth('login')">登录</a-link>
      <a-link class="nav-item" @click.prevent="openAuth('register')"
        >注册</a-link
      >
    </div>
    <div class="right">
      <a-button type="primary" size="small" @click="$router.push('/submit')"
        >上传模板</a-button
      >
    </div>
  </div>
  <a-modal
    :visible="authVisible"
    :footer="false"
    :width="900"
    :mask-closable="true"
    unmount-on-close
    :modal-style="{ position: 'relative' }"
    class="custom-auth-modal"
    @cancel="authVisible = false"
  >
    <div class="auth-modal">
      <div class="auth-left">
        <div class="welcome">欢迎！</div>
        <div class="brand">V.</div>
        <div class="smile">:)</div>
        <div class="switch-tip">
          {{ authMode === 'login' ? '还不是成员？' : '已经注册了？' }}
          <a-link
            @click="authMode = authMode === 'login' ? 'register' : 'login'"
          >
            {{ authMode === 'login' ? '立即注册' : '去登录' }}
          </a-link>
        </div>
      </div>
      <div class="auth-right">
        <a-typography-title
          :heading="1"
          :style="{ marginTop: '0', marginBottom: '24px' }"
        >
          {{ authMode === 'login' ? '登录' : '注册' }}
        </a-typography-title>
        <a-form layout="vertical">
          <a-form-item
            field="email"
            label="电子邮件或用户名"
            style="margin-top: 20px"
          >
            <a-input
              v-model="auth.email"
              placeholder="电子邮件或用户名"
              style="margin-top: 20px"
            />
          </a-form-item>
          <a-form-item field="password" label="密码" style="margin-top: 20px">
            <a-input-password
              v-model="auth.password"
              placeholder="密码"
              style="margin-top: 20px"
            />
          </a-form-item>

          <a-checkbox v-if="authMode === 'login'" v-model="auth.remember"
            >保持登录状态</a-checkbox
          >
          <a-button
            type="primary"
            long
            :style="{ marginTop: '12px' }"
            style="margin-top: 40px"
          >
            {{ authMode === 'login' ? '立即登录' : '立即注册' }}
          </a-button>
        </a-form>
        <div class="social">
          <span>或使用</span>
          <a-space :size="10" style="margin-top: 8px; display: block">
            <a-button shape="round">G 谷歌</a-button>
            <a-button shape="round">F 脸书</a-button>
            <a-button shape="round">X 响</a-button>
          </a-space>
        </div>
      </div>
    </div>
  </a-modal>
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

  type AuthMode = 'login' | 'register';
  const authVisible = ref(false);
  const authMode = ref<AuthMode>('login');
  const auth = ref({ email: '', password: '', confirm: '', remember: true });
  const openAuth = (mode: AuthMode) => {
    authMode.value = mode;
    authVisible.value = true;
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

<style scoped>
  .auth-modal {
    display: grid;
    grid-template-columns: 1.2fr 1fr;
    min-height: 560px; /* 增加整体高度 */
  }
  .auth-left {
    background: #f5f5f5;
    border-radius: 8px;
    margin-right: 16px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100%; /* 确保左侧区域占满高度 */
  }
  .welcome {
    font-size: 20px;
    margin-bottom: 20px;
  }
  .brand {
    font-size: 56px;
    font-weight: 800;
  }
  .smile {
    font-size: 48px;
    margin: 10px 0 40px;
  }
  .switch-tip {
    color: var(--color-text-2);
  }
  .auth-right {
    padding-left: 20px; /* 增加内边距 */
    padding-right: 40px;
    padding-top: 80px;
    padding-bottom: 0px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 100%; /* 确保右侧区域占满高度 */
  }
  .social {
    margin-top: 20px; /* 增加社交按钮上边距 */
    color: var(--color-text-2);
  }
</style>

<style>
  /* 放大并固定关闭按钮到右上角 */
  .custom-auth-modal .arco-modal-close-btn {
    position: absolute;
    top: 16px !important;
    right: 16px !important;
    width: 36px !important;
    height: 36px !important;
    z-index: 1001;
  }
  .custom-auth-modal .arco-modal-close-icon {
    font-size: 22px !important;
  }
  /* 调整模态框内容区域高度 */
  .custom-auth-modal .arco-modal-body {
    padding: 0;
  }
</style>
