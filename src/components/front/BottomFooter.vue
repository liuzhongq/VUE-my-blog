<template>
  <div class="footer-containe">
    <div class="rights">
      <p>Copyright ©  {{ new Date().getFullYear() }} Liuzhongqing's Blog</p>
    </div>
    <div class="to-admin">
      <router-link tag="a" to="/login">后台登陆</router-link>
    </div>
    <div class="history-version">
      <a href="http://192.168.3.180:8081/">历史版本</a>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  @import '@/common/css/variable.scss';
  .footer-containe {
    height: 32px;
    line-height: 32px;
    font-size: 12px;
    color: $color-white;
    display: flex;
    justify-content: center;
    .rights {
      margin-right: 10px;
    }
    .history-version {
      margin-left: 10px;
    }
    a {
      color: $color-white;
      &:hover {
        color: $color-blue;
      }
    }
  }
</style>
