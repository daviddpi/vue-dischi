<template>
    <div>
        <div class="bg-logo">
            <img src="../assets/img/logo.png" alt="Logo spotify">
        </div>

        <div class="bg-main">
            <div class="container">
                <div class="row row-cols-1 row-cols-sm-3 row-cols-md-5 container-box-music">
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                    <div class="col">
                        <div class="box-music"></div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import axios from 'axios'

export default {
    data(){
        return{

        }
    },

    components: "",
    mounted(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music').then( (response) => {
        const result = response;
        console.log(result);
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

.box-music{
    height: 300px;
    margin: 15px;
    background-color: $primaryColor;
}

</style>