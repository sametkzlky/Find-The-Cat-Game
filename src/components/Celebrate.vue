<template>
    <div class="container">
        <h1>Tebrikler Bildiniz!!!</h1>
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
template{
    padding: 0;
    margin: 0;
}
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
}
h1{
    font-family: sans-serif;
    font-size: 35px;
    font-weight: bold;
    color: green;
    opacity: .5s;
}
button{
    padding: 10px 30px;
    font-size: 15px; 
    cursor: pointer;
    color: red;
    border-radius: 5px;
    border: solid 1px green;
    background: none;
}
button:hover{
    transition: 1s;
    background-color: darkgreen;
    color: #fff;
}
</style>