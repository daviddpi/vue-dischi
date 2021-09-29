<template>
    <div>
        <div class="col">
            <div class="box-music text-center">
                <img :src="source" :alt="autore">
                <h3>{{ titolo }}</h3>
                <h5>{{ autore }}</h5>
                <h6>{{ anno }}</h6>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        source: String,
        titolo: String,
        autore: String,
        anno: String,
    }
}
</script>

<style lang="scss">
@import '../style/general.scss';

.col{
    padding: 0;
}

.box-music{
    height: 350px;
    margin: 15px;
    background-color: $primaryColor;

    img{
        max-width: 80%;
        padding-top: 15px;
    }

    h3{
        color: white;
        font-size: 1.3rem;
        text-transform: uppercase;
        padding: 15px;
    }

    h5, h6{
        color: gray;
        margin-bottom: 0;
    }
}





</style>