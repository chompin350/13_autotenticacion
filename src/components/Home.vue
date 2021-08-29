<template>
  <el-container>
    <el-header class="text-left" type="info">
      <img src="@/assets/image.png" alt="Logo">
      Menu principal
      <el-button
        type="info"
        icon="el-icon-back"
        square
        @click="logout"
        title="logout"
      >Logout</el-button>
    </el-header>
    <el-container>
      <el-aside width="200px">
        <el-menu :default-openeds="['1', '3']">
          <el-submenu index="1">
            <template slot="title"
              ><i class="el-icon-menu"></i>Men&uacute;</template
            >
            <el-submenu index="1-4">
              <template slot="title">Usuarios</template>
              <el-menu-item index="1-4-1">Mantenedor</el-menu-item>
            </el-submenu>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-main>
        <h3>Desafío - Creación de autentificación con Vue Router </h3>
        <div class="container text-left">
          Se  requiere  crear  un  sistema  de  autenticación  mediante  vue-router,  este  debe  tener  dos componentes  el  componente  Login  y  el  componente Home conectados con un router, y el cual  tendrá  un  guard  global  que  realice  la  función  de  un  middleware,  con  esto  debe  ser posible  ingresar  al  home  únicamente  si  el  usuario  está  autenticado,  y  debe  ser  posible ingresar al login únicamente si el usuario no está autenticado. La autenticación debe ser por Firebase. 
        </div>
      </el-main>
    </el-container>
  </el-container>
</template>
<script>
import Firebase from "firebase";
export default {
  data() {
    return {};
  },
  methods: {
    logout() {
      Firebase.auth()
        .signOut()
        .then((accept) => {
          this.$router.push("login");
        });
    },
  },
};
</script>



<style lang="scss" scoped>
.el-header {
  background-color: #767980;
  color: #fff;
  line-height: 60px;
  .el-button {
    float: right;
    margin-top: 10px;
  }
}
.el-aside {
  color: #333;
}
</style>

