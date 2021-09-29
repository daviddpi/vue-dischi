<template>
    <div>
        <div class="bg-logo">
            <img src="../assets/img/logo.png" alt="Logo spotify">
        </div>

        <div class="bg-main">
            <div class="container">
                <div v-if="load" class="row row-cols-1 row-cols-sm-3 row-cols-md-5 container-box-music">
                    <CardMusic v-for="(item, index) in arrayMusic" :key="index" :source="item.poster" :titolo="item.title" :autore="item.author" :anno="item.year"/>
                </div>

                <div v-else class="row">
                    <Loading />
                </div>
            </div> 
        </div>

    </div>
</template>

<script>
import axios from 'axios'
import CardMusic from './CardMusic.vue'
import Loading from './Loading.vue'

export default {
    data(){
        return{
            arrayMusic: [],
            load: false,
        }
    },

    components: { 
      CardMusic,
      Loading,
    },

    mounted(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music').then( (response) => {
        const result = response.data.response;
        console.log(result);
        this.arrayMusic = result.slice();

            setTimeout( ()=> {
                this.load = true;
            }, 3500);

        })
    }
}
</script>

<style lang="scss">
@import '../style/general.scss';

.bg-main{
    background-color: $secondaryColor;
}


.bg-logo{
    height: 50px;
    width: 100%;
    background-color: $primaryColor;

    img{
        max-width: 40px;
        margin: 5px 20px;
    }
}

.container-box-music{
    display: flex;
    flex-wrap: wrap;
    min-height: 100vh;
    align-content: center;

    .col{
        padding: 0;
    }
}

</style>