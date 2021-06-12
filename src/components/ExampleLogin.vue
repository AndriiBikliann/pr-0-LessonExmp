<template>
    <div>
      <label>
      Введіть логін
      <input type="text" v-model="userLogin">
      </label> <br>
      <label>
      Введіть пароль
      <input type="password" v-model="userPass">
      </label> <br>
      <button @click="checkPass">Go</button>
      <img :src="imageSrc" alt="picture" v-if="checkPass">
    </div>
</template>

<script>
    export default {
        name : 'ExampleLogin',
        props: {
            imageSrc: {
                type: String,
                default:"https://image.freepik.com/free-vector/smile-logo-template_8163-40.jpg"
            }
        },
        data () {
            return {
               userLogin:"",
               userPass :"",
               authResultMessage: null,
               loginBase : [
                  {
                  login: "Ivan", 
                  pass:"111"
                  },
                  {
                  login: "Petro", 
                  pass:"222"
                  },
                  {
                  login: "Roma", 
                  pass:"333"
                  },
                  {
                  login: "Stas", 
                  pass:"444"
                  }, 
                 ],
            };
        },
        methods: {
        checkPass() {
      if (
        this.loginBase.some(
          (item) => this.userLogin == item.login && this.userPass == item.pass
          )
        )
          this.authResultMessage = "Вірно"
          else this.authResultMessage = "Некоректний логін або пароль!"
      }
    }
 }
</script>

<style lang="scss" scoped>

</style>