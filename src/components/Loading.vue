<template>

   <div class="container-loading">
        <div class="loading">
            <img src="../assets/img/logo.png" alt="Logo Spotify">
            <h1>Caricamento...</h1>
        </div>
   </div>
    
</template>

<script>
export default {

}
</script>

<style lang="scss">
@import '../style/general.scss';

.container-loading{
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

.loading{
    color: white;

    img{
        animation: rotation 0.7s linear infinite alternate;
        margin-bottom: 15px;
    }
}

@keyframes rotation{
    from{transform: scale(1);}
    to{transform: scale(1.3);}
}

</style>