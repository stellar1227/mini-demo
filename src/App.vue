<template>
  <div id="app">
    <el-container direction="vetical">
      <el-header class="header" >
          <el-button class="btn_menu" :icon="isCollapse ? 'el-icon-s-unfold' : 'el-icon-s-fold'" @click="isCollapse = !isCollapse" circle></el-button>
          <h1 class="logo"><a href=""><img src="./assets/logo.png" alt="logo" /></a></h1><!-- href에 페이지link, src에 이미지 주소 -->
      </el-header>
      <el-container>
        <el-aside width="auto" class="sidemenu">
          <el-menu default-active="1" class="sidemenu_list" @open="handleOpen" @close="handleClose" :collapse="isCollapse">
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span slot="title">Navigator One</span>
            </template>
            <el-menu-item-group>
              <span slot="title">Group One</span>
              <el-menu-item index="1-1">item one</el-menu-item>
              <el-menu-item index="1-2">item two</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="Group Two">
              <el-menu-item index="1-3">item three</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-menu-item index="2">
            <i class="el-icon-menu"></i>
            <span slot="title">Navigator Two</span>
          </el-menu-item>
          <el-menu-item index="3">
            <i class="el-icon-document"></i>
            <span slot="title">Navigator Three</span>
          </el-menu-item>
          <el-menu-item index="4">
            <i class="el-icon-setting"></i>
            <span slot="title">Navigator Four</span>
          </el-menu-item>
        </el-menu>
        </el-aside>
        
        <el-main>ddd</el-main> 
      </el-container>
      
    </el-container>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
      return {
        isCollapse : true,
      };
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    }
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
