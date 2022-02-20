<template>
  <div id="app">
    <el-container direction="vetical">
      <el-header class="header" >
          <el-button class="btn_menu" :icon="isCollapse ? 'el-icon-s-unfold' : 'el-icon-s-fold'" @click="isCollapse = !isCollapse" circle></el-button>
          <h1 class="logo"><a href=""><img src="./assets/logo.png" alt="logo" /></a></h1><!-- href에 페이지link, src에 로고 이미지 주소 -->
      </el-header>
      <el-container>
        <el-aside width="auto" class="sidemenu">
          <el-menu default-active="1" class="sidemenu_list" :collapse="isCollapse">
          <el-submenu index="1"><!-- 하위메뉴가 있는 케이스 -->
            <template slot="title">
              <i class="el-icon-location"></i>
              <span slot="title">Navigator One</span><!-- 1depth menu명 -->
            </template>
            <el-menu-item index="1-1" @click="fetchData('1-1')">item one</el-menu-item><!-- 2depth menu명 -->
            <el-menu-item index="1-2" @click="fetchData('1-2')">item two</el-menu-item>
            <el-menu-item index="1-3" @click="fetchData('1-3')">item three</el-menu-item>
          </el-submenu><!-- //하위메뉴가 있는 케이스 -->
          <el-menu-item index="2" @click="fetchData('2')"><!-- 하위메뉴 없는 단일 케이스 -->
            <i class="el-icon-menu"></i>
            <span slot="title">Navigator Two</span>
          </el-menu-item><!-- //하위메뉴 없는 단일 케이스 -->
          <el-menu-item index="3" @click="fetchData('3')">
            <i class="el-icon-document"></i>
            <span slot="title">Navigator Three</span>
          </el-menu-item>
          <el-menu-item index="4" @click="fetchData('4')">
            <i class="el-icon-setting"></i>
            <span slot="title">Navigator Four</span>
          </el-menu-item>
        </el-menu>
        </el-aside>
        
        <el-main>
          {{ content }}
        </el-main> <!-- data parsing {{ data name }} -->
      </el-container>
      
    </el-container>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  components: {
  },
  data() {
      return {
        isCollapse : true,
        pageData : {},
        content : 'dummy기본텍스트',
      };
  },
  methods: {
    fetchData : function(url){
      //나중에 api 붙일때 파일 이름부분 url로 수정해야함 현재는  메뉴 :index속성으로 파일명 매치함
      //파일형태는 JSON, 현재 정적파일의 위치는 public
      //추후는 data 구조에 따라서 파라미터 설정이 필요해영 내용을 어떻게 구성할지 알려주세요 
      axios.get(`${url}.json`)
          .then((res) => {
            console.log(res);
            this.pageData = res.data;
            this.content = res.data.content;
          })
          .catch((ex) => {
            console.log('error', ex)
          })
    },
  }
}
</script>

<style lang="scss">

*{
  margin:0; 
  padding:0;
}

html{
  background:rgba(33,33,33,0.98);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #fafafa;

}

.header{
  padding:0 20px 0 0; 
  border-bottom:1px solid rgba(255,255,255, 0.1);
  .btn_menu{
    margin-right:10px;
    vertical-align: middle;
    padding:0;
    background:transparent;
    border:0;
    width:60px;
    height:60px;
    i{
      font-size:24px;
      color:#fff;
    }
  }
  .logo{
    display: inline-block;
    font-size:0;
    vertical-align: middle;
    img{
      height:26px;
    }
  }
}

.sidemenu{
  height:calc(100vh - 60px);
  border-right:1px solid rgba(255,255,255, 0.1);
  .sidemenu_list:not(.el-menu--collapse){
    width:200px;
  }
  .el-menu{
    background:transparent;
    border-right:0;
  }
  .el-menu-item{
    color:#fafafa;
    &:focus, &:hover{
      color:#353535;
      [class^=el-icon-]{
        color:#353535;
      }
    }
  }
  .el-menu-item [class^=el-icon-]{
    width:auto!important;
    color:#fafafa;
    font-size:22px;
  }
  .el-submenu [class^=el-icon-]{
    width:auto!important;
    color:#fafafa;
    i{
      color:#fafafa;
      font-size:22px;
    }
  }
  .el-submenu__title{
    &:focus, &:hover{
      color:#353535;
      i{
        color:#353535;
      }
    }
    color:#fafafa;
    i{
      font-size:22px;
    }
  }
  .el-menu--collapse{
    width:60px;
  }
}

</style>
