<template>
    <div>
      <label>
      Введіть логін
      <input type="text" v-model="userLogin">
      </label> <br>

      <label>
      Введіть пароль
      <input type="password" v-model.number="userPass">
      </label> <br>

      <button @click="checkPass">Go</button>

      <div v-if="checkAutorize">
          <div v-if="checkAutorize===loginValue.CORRECT">
            <img src="imageSrc" alt="picture">
          </div>
          <div v-else-if="checkAutorize===loginValue.INCORRECT_IVAN" :class="getClass()"> Невірний логін </div>
          <div v-else :class="getClass()"> Невірний логін і пароль</div>
       </div>
    </div>
</template>

<script>
import { loginValue } from './settings.js'
    export default {
        name : 'ExampleLogin',
        props: {
            imageSrc: {
                type: String,
                default:"https://image.freepik.com/free-vector/smile-logo-template_8163-40.jpg"
            },
            userDataArray: {
                type:Array,
                default: ()=>[]
            }

        },
        data () {
            return {
               userLogin:null,
               userPass :null,
               checkAutorize: null,
               loginValue,
         }
        },
        methods: {
          checkPass () {
              if(
                  this.userDataArray.some(
                      (item)=> this.login===item.login&& this.password===item.password
                  )
                ) {
              this.checkAutorize = loginValue.CORRECT
              return;
                }
              if (this.login === 'Ivan')
                  this.value = loginValue.INCORRECT_IVAN;
                  else
                  this.value = loginValue.INCORRECT
              
        },
        getClass() {
            if (this.userLogin === "Ivan") {
                return (this.loginValue = "blue");
            }
            else {
                return (this.loginValue = "red")
            }
        }
    }
 }
</script>

<style lang="css" scoped>
.red {
    color: red;
}
.blue {
    color: blue;
}
</style>
