<template>
  <el-carousel height="800px" class="el-carousel">
    <el-carousel-item class="carosel-inner" v-for="(item, index) in bannerList" :key="index">
      <div class="carousel-wrap">
        <div class="carousel-caption">
          <h1 class="bounce">{{ item.title }}</h1>
          <ul>
            <li v-for="(descItem, descIndex) in item.descList" :key="`desc-${index}-${descIndex}`">
              {{ descItem }}
            </li>
          </ul>
          <!--<el-button round @click="goFile">{{ item.btn }}</el-button>-->
          <!--<div class="version-wrapper">-->
            <!--<a-->
            <!--  class="version-item"-->
            <!--  v-for="(linkItem, linkIndex) in item.linkList"-->
            <!--  :key="`link-${index}-${linkIndex}`"-->
            <!--  :href="linkItem.link"-->
            <!--  target="_blank"-->
            <!--&gt;-->
            <!--  <span class="version-number">{{ linkItem.versionNo }}</span>-->
            <!--  <span>{{ linkItem.date }} &gt;&gt;</span>-->
            <!--</a>-->
          <!--</div>-->
          <div class="carousel-img_small">
            <img :src="item.bannerImg" />
          </div>

        </div>
        <div class="carousel-img_big">
          <img :src="item.bannerImg1" />
        </div>
      </div>
    </el-carousel-item>
  </el-carousel>
</template>

<script>
export default {
  name: 'Banner',
  data() {
    return {
      bannerList: [
        {
          title: '一款功能齐全的文件管理系统',
          descList: ['文件传输，安全快捷', '在线编辑，所见即所得', '回收站，防止文件误删'],
          btn: '开源免费，立即体验',
          linkList: [
            {
              versionNo: '最新版本v1.4.0',
              date: '2021年5月14日发布',
              link: 'https://gitee.com/qiwen-cloud/qiwen-file'
            }
          ],

          bannerImg1: require('@/assets/images/home/banner/banner2.svg'),
          bannerImg: require('@/assets/images/home/banner/banner1.png')
        }
      ]
    }
  },
  methods: {
    // 跳转到网盘页面
    goFile() {
      this.$router.push({ name: 'File', query: { filePath: '/', fileType: 0 } })
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl';

.el-carousel {
  width: 100%;
  display: block;
  background: linear-gradient(to right, #409EFF, #79bbff);

  .carosel-inner {
    width: 100%;
    height 100%;

    .carousel-wrap {
      position: relative;
      margin: 0 auto;
      width: 85%;
      height: 100%;

      .carousel-caption {
        position: absolute;
        left: 30px;
        top: 100px;
        text-shadow: none;
        max-width: 550px;
        color: #fff;
        text-align: center;

        h1 {
          font-weight: normal;
          margin: 0;
          font-size: 30px;
          animation-delay: 1s;
        }

        ul {
          padding: 25px 0 25px 20px;

          li {
            line-height: 2.2;
            font-size: 15px;
          }
        }

        //>>> .el-button {
        //  border-width: 2px;
        //  background: transparent;
        //  color: #fff;
        //
        //  &:hover {
        //    border-color: transparent;
        //    background: $Warning;
        //  }
        //}

        //.version-wrapper {
        //  margin: 0 0 10px;
        //
        //  .version-item {
        //    display: inline-block;
        //    margin: 50px 0 0 18px;
        //    color: rgba(255, 255, 255, 0.8);
        //
        //    &:hover {
        //      text-decoration: underline;
        //      color: #fff;
        //    }
        //
        //    .version-number {
        //      margin-right: 16px;
        //    }
        //  }
        //}
      }

      .carousel-img_small {
        max-width: 500px;
        position: absolute;
        right: 0px;
        top: 80px;
        z-index:-1;

        img {
          max-width: 120%;
          vertical-align: middle;
        }
      }
      .carousel-img_big {
        //max-width: 580px;
        position: absolute;
        right: 0px;
        top: 0px;
        z-index:-1;

        img {
          //max-width: 100%;
          vertical-align: middle;
        }
      }
    }
  }
}
</style>
