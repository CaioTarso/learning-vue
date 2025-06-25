<template>
    <section class="video">
        <h2>Não sabe basquete? não tem Problema</h2>
        <p>Assista a esse vídeo e aprenda tudo sobre o basquete</p>
        <div class="video-conatiner">
            <iframe width="897" height="505" src="https://www.youtube.com/embed/TvdgRhHVF0I" 
            title="EXPLICANDO QUAIS SÃO AS POSIÇÕES DO BASQUETE (Guia Completo)" frameborder="0" 
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" 
            allowfullscreen></iframe>
        </div>
    </section>
</template>

<script>
export default {
    name: 'VideoSection',
}
</script>

<style>
.video {
    padding: 50px;
    text-align: center;
    
}
.video-conatiner {
    display: flex;
    justify-content: center;
    align-items: center;
}
.video-conatiner iframe {
    max-width: 100%;
    height: 500px;
}
.video h2 {
    margin-bottom: 10px;
    font-size: 2em;
}
.video p {
    margin-bottom: 20px;
    font-size: 1.2em;
}

</style>