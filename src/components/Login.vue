<template>
  <div id="login" class="container">
    <img src="../assets/image.png" class="img-inicial" />
    <el-form label-width="100px" class="form-login" :model="formLabelAlign">
      <el-input
        placeholder="Correo electrónico"
        v-model="formLabelAlign.user"
      ></el-input>
      <el-input
        type="password"
        placeholder="Contraseña"
        v-model="formLabelAlign.password"
        autocomplete="off"
      ></el-input>
      <el-button type="primary" class="ingresar-login" @click="login"
        >Ingresar</el-button
      >
    </el-form>
    <el-divider></el-divider>
    <article class="message">
      <el-card class="box-card">
        <template #header>
          <el-divider></el-divider>
          <div class="message-header">
            <p>Mensaje</p>
          </div>
          <div class="message-body">
            Para poder ingresar tenemos el correo
            <strong>ecamp@gmail.com</strong> contraseña <strong>123123</strong>.
          </div>
        </template>
      </el-card>
    </article>
  </div>
</template>

<script>
import Firebase from "firebase";
import FirebaseConfig from "@/configs/Firebase";
import { Message } from "element-ui"; // Initialize Firebase
Firebase.initializeApp(FirebaseConfig);
export default {
  data() {
    return {
      formLabelAlign: {
        user: "",
        password: "",
      },
    };
  },
  methods: {
    login() {
      Firebase.auth()
        .signInWithEmailAndPassword(
          this.formLabelAlign.user,
          this.formLabelAlign.password
        )
        .then(
          (accept) => {
            this.$router.push("home");
          },
          (reject) => {
            this.$message({
              showClose: true,
              message: reject.message,
              type: "error",
            });
          }
        );
    },
  },
};
</script>

<style lang="scss" scoped>
#login {
  padding: 60px;
  .ingresar-login {
    width: 100%;
  }
  .img-inicial,
  .form-login {
    display: block;
    margin: auto;
  }
  .form-login {
    width: 300px;
    .el-input {
      margin-bottom: 10px;
    }
  }
}

</style>