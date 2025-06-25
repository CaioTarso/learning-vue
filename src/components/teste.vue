<template>
    <header>
        <h1>Portal Basquete</h1>
        <ul>
            <li><a href="https://www.espn.com.br/nba/calendario">Próximos jogos</a></li>
            <li><a href="https://www.youtube.com/nbabrasil">Vídeos</a></li>
            <li><a href="https://hoop-snake-quiz-challenge.lovable.app">Jogo da cobrinha</a></li>
        </ul>
    </header>
</template>

<script>
export default {
    name: 'TesteComponent',
}
</script>

<style>

*{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
}

header {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    padding: 20px;
    background-color: #42b983;
    color: white;
    text-align: center;
}
ul {
    list-style-type: none;
    
 
}
li {
    display: inline-block;
    margin: 0 10px;
    
}
a {
    color: white;
    text-decoration: none;
}
</style>