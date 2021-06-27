<template>
    <div :class="messageClass">
       <span v-if="isPensioner"> Можете відпочивати</span>
       <span v-else-if="userAge===21">В Одесу</span>
       <span v-else> Вам потрібно працювати</span>
    </div>
</template>

<script>
    export default {
        name : 'AgeSolver',
        props : {
            userAge: {
                type : Number,
                default : 0,
            },
            pensionerAge: {
                type: Number,
                default: 65,
            }
        },
        computed : {
            isPensioner(){
            return this.userAge>this.pensionerAge
            },
            messageClass(){
            return this.isPensioner?'red':'green'
            }
        }

    }
</script>

<style lang="css" scoped>
.red {
    color: red;
}
.green {
    color: green;
}
</style>