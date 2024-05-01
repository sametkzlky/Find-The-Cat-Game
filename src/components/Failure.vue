<template>
    <div class="container">
        <h1>Maalesef Bilemediniz!!!</h1>
        <button @click="newGame">Yeni Oyun</button>
    </div>
</template>
<script>
export default{
    methods : {
        newGame(){
            this.$emit("activeComponentEvent","app-game-cards")
        }
    }
}
</script>
<style scoped>
.container{
    position: absolute;
    top: 0px;
    left: 0px;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: darkred;
}
h1{
    font-family: sans-serif;
    font-size: 35px;
    font-weight: bold;
    color: white;
}
button{
    padding: 10px 30px;
    font-size: 15px; 
    cursor: pointer;
    color: red;
    border-radius: 5px;
    border: none;
}
button:hover{
    transition: 1s;
    background-color: rgb(129, 183, 129);
    color: #fff;
}
</style>