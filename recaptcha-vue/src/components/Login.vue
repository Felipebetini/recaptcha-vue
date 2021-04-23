<template>
  <div class="body">
    <div class="container divLogin">
      <h2 class="container-fluid hLogin">Faca seu login</h2>
      <form class="form">
        <input type="text" id="usuario" placeholder="Usuario" />
        <input type="password" id="senha" placeholder="Senha" />
        <vue-recaptcha
          sitekey="Your key here"
          class="recaptcha"
          @verify="recaptchaIsOn = true"
          :style="colorRed"
        />
        <div class="mb-3 mt-1" :style="downText">
          {{ recaptchaText }}
        </div>
        <button id="login-button" @click="submit">Login</button>
      </form>
    </div>
  </div>
</template>

<script>
import VueRecaptcha from "vue-recaptcha";
export default {
  components: { VueRecaptcha },
  data: () => ({
    recaptchaIsOn: false,
    recaptchaText: "",
    downText: {
      color: "#ff5252",
      fontSize: "12px",
      padding: "0 12px",
    },
    isActive: true,
    colorRed: "",
  }),
  submit() {
    if (this.recaptchaIsOn === false) {
      this.recaptchaText = "Por favor faça o recaptcha";
      this.colorRed = "border: medium solid #ff5252";
    }
  },
  methods: {
    async recaptcha() {
      // (optional) Wait until recaptcha has been loaded.
      await this.$recaptchaLoaded();
    },
  },
};
</script>

<style scoped>
@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.divLogin {
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
  color: white;
  font-weight: bold;
  border: 3px solid #f1f1f1;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  padding: 20px;
  text-align: center;
  height: 22vw;
  border-radius: 50px;
  box-shadow: 10px 10px 5px black;
  padding: 4vw;
}

form {
  padding: 2vwx 0;
  position: relative;
  z-index: 2;
}
form input {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  outline: 0;
  border: 1px solid rgba(255, 255, 255, 0.4);
  background-color: rgba(255, 255, 255, 0.2);
  width: 280px;
  border-radius: 3px;
  padding: 10px 15px;
  margin: 0 auto 40px auto;
  display: block;
  text-align: center;
  font-size: 18px;
  color: white;
  -webkit-transition-duration: 0.25s;
  transition-duration: 0.25s;
  font-weight: 300;
}
form input:hover {
  background-color: rgba(255, 255, 255, 0.4);
}
form input:focus {
  background-color: white;
  width: 300px;
  color: #000000;
}

form button {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  outline: 0;
  background-color: white;
  border: 0;
  padding: 10px 15px;
  color: #153a07;
  border-radius: 3px;
  width: 250px;
  cursor: pointer;
  font-size: 18px;
  -webkit-transition-duration: 0.25s;
  transition-duration: 0.25s;
  margin-bottom: 4vw;
  width: 250px;
}
form button:hover {
  background: linear-gradient(-45deg, #6cee52, #e73c3c, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient 15s ease infinite;
  color: white;
}

.hLogin {
  margin-bottom: 2vw;
  margin-top: 1vw;
}

.btnLogar {
  width: 10vw;
  margin-top: 1vw;
  margin-bottom: 2vw;
  box-shadow: 5px 5px 2px black;
}

.btnCadastro {
  width: 10vw;
  box-shadow: 5px 5px 2px black;
}

.divCadastro {
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
  color: white;
  font-weight: bold;
  border: 3px solid #f1f1f1;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  width: 25%;
  padding: 20px;
  text-align: center;
  height: 30vw;
  border-radius: 50px;
  text-align: center;
  padding-top: 3vw;
  font-size: 1.5vw;
  box-shadow: 10px 10px 5px black;
}

.hCadastros {
  margin-bottom: 2vw;
  font-weight: bold;
}

.voltar {
  text-decoration: none;
  display: block;
  color: white;
}

.divHead {
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
  color: white;
  font-weight: bold;
  border: 3px solid #f1f1f1;
  position: absolute;
  top: 4%;
  width: 50vw;
  text-align: center;
  height: 22vw;
  border-radius: 50px;
  text-align: center;
  padding-top: 1vw;
  font-size: 1.5vw;
  box-shadow: 10px 10px 5px black;
  left: 23vw;
}

.divRegistro {
  text-align: center;
}

.divTable {
  width: 45vw;
}

@media screen and (max-width: 500px) {
  .divLogin {
    height: 60%;
  }
  .hLogin {
    margin-top: 2vw;
  }
}
.recaptcha {
  margin: auto;
  display: inline-block;
  margin-bottom: 2vw;
}
</style>
