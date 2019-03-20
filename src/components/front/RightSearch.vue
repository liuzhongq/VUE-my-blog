<template>
  <div class="right-search" v-if="!mobileFlag">
    <div class="self-info">
      <div class="avatar-wrapper">
        <img class="avatar" src="../../assets/selfInfo.jpg" alt="">
        <div class="message">
          <p>刘仲庆</p>
          <p>前端小菜鸟</p>
        </div>
      </div>
      <div class="descr-wrapper">
        <p>好好学习，天天向上</p>
      </div>
      <div class="social-wrapper">
        <a href="https://github.com/liuzhongq" target="_blank">
          <icon-font class="social-icon" icon="icon-github" fontSize="42"></icon-font>
        </a>
        <el-popover
          placement="bottom"
          trigger="hover">
          <img class="wechat" src="../../assets/Wechat.a604047e.jpg" alt="">
          <template slot="reference">
            <icon-font class="social-icon" icon="icon-weixin" fontSize="42"></icon-font>
          </template>
        </el-popover>
      </div>
    </div>
    <div class="self-info">
      <el-container class="tags">标签 : </el-container>
      <div class="tag-all">
        <el-tag v-for="tag in tags" :key="tag.id">{{ tag.name }}</el-tag>
      </div>
    </div>
  </div>
</template>

<script>
  import IconFont from '@/components/Iconfont'
  import { apiUrl } from '@/serviceAPI.config.js'
  import { mapGetters } from 'vuex'
  export default {
    data() {
      return {
        hotArticle: [],
        tags: [],
        tagSel: [],
        tagIdMax: 1,
      }
    },
    computed: {
      ...mapGetters([
        'mobileFlag'
      ])
    },
      created() {
          this.newTagId = 0
          let query = this.$route.query;
          this.$http.post(apiUrl.getTag).then((res) => {
              if (res.data.code === 200) {
                  this.tags = res.data.message;
                  this.tags.forEach(ele => {
                      ele.id = ele._id
                  })
              }
          })
          if (query.id) {
              this.id = query.id
              this.$http.post(apiUrl.getArticle, {
                  data: {id: query.id, markdown: true}
              }).then((res) => {
                  const message = res.data.message
                  if (res.data.code === 200) {
                      this.title = message[0].title
                      this.tagSel = message[0].tag
                      this.content = message[0].content
                      this.tagSel.forEach(ele => {
                          ele.id = ele._id
                      })
                      this.originTitle = message[0].title
                  } else {
                      this.$message.error(message)
                  }
              })
          }
      },
    methods: {
        getHotArticle() {
            this.$http.post(apiUrl.getHotArticle, {
                data: {hot: true}
            }).then((res) => {
            })
        },
    },
    components: {
      IconFont
    }
  }
</script>

<style lang="scss" scoped>
  @import '@/common/css/variable.scss';
  .right-search {
    width: 30%;
    margin-left: 20px;
    opacity: 0.8;
  }

  .self-info {
    text-align: left;
    background: $color-white;
    margin-bottom: 10px;
    padding: 10px;
    border-radius: 3px;
    font-size: 14px;
    p {
      padding: 5px 0;
    }
    .tags{
        margin-bottom: 10px;
    }
    .avatar-wrapper {
      display: flex;
      .avatar {
        width: 100px;
        height: 100px;
        margin-right: 10px;
      }
    }
    .social-wrapper {
      margin-top: 10px;
      .social-icon {
        cursor: pointer;
        margin-right: 10px;
        &:hover {
          color: $color-blue;
        }
      }
      .wechat {
        width: 200px;
        height: 200px;;
      }
    }
  }
</style>
