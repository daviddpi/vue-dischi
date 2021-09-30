<template>
    <div>
        <div class="bg-logo d-flex justify-content-lg-between align-items-center">
            <img src="../assets/img/logo.png" alt="Logo spotify">

            <div class="d-flex">
                <h6>Seleziona genere</h6>
                <select id="genre-music-select">
                        <SelectGenre @choose="changeGenre" v-for="(element, index) in genreMusic" :key="index" :genre="element"></SelectGenre>
                </select>
            </div>
            
        </div>

        <div class="bg-main">
            <div class="container">

                <div v-if="load == true" class="row row-cols-1 row-cols-sm-3 row-cols-md-5 container-box-music">
                    <CardMusic v-for="(item, index) in filteredMusic" :key="index" :source="item.poster" :titolo="item.title" :autore="item.author" :anno="item.year"/>
                </div>

                <div v-else-if="!load" class="row">
                    <Loading />
                </div>

                <div v-else-if="load == 'vuoto'"> 
                    <h1 class="emptyArray mb-0 text-center text-white">Mi dispiace, non ci sono contenuti da mostrare 😅</h1>
                </div>
            </div> 
        </div>

    </div>
</template>

<script>
import axios from 'axios'
import CardMusic from './CardMusic.vue'
import Loading from './Loading.vue'
import SelectGenre from './SelectGenre.vue'

export default {
    data(){
        return{
            arrayMusic: [],
            load: false,
            myAPI: 'https://flynn.boolean.careers/exercises/api/array/music',
            genreMusic: [],
            genreSelect: "",
            arrayMusicFiltered: [],
        }
    },

    methods: {
        addGenreSelect(){
            this.arrayMusic.forEach( element => {
                if(!this.genreMusic.includes(element.genre)){
                    this.genreMusic.push(element.genre);
                }
            })
            return this.genreMusic;
        },

        changeGenre(genre){
            this.genreSelect = genre;
        },
        

        // filteredMusic(){
        //     this.arrayMusicFiltered = this.arrayMusic.filter( element => {
        //         return element.genre == this.genreSelect;
        //     })
        // }
    },

    components: { 
      CardMusic,
      Loading,
      SelectGenre,
    },

    mounted(){
        axios.get(this.myAPI).then( (response) => {
        const result = response.data.response;
            console.log(result);
            this.arrayMusic = result.slice();
            //in caso l'array fosse vuoto, verrà visualizzato un messaggio a schermo che informi l'utente
            // this.arrayMusic = "";
            if(this.arrayMusic.length > 0){
                setTimeout( () => {
                    this.load = true;  
                }, 2000);
            } else{
                setTimeout( () => {
                    this.load = "vuoto";
                }, 2000);
            }
            this.addGenreSelect();
            this.changeGenre();
            // this.filteredMusic();
        });
    },

    computed: {
        filteredMusic(){
            return this.arrayMusic.filter( element => {
                return element.genre == this.genreSelect;
            })
        }
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

    h6{
        color: white;
        padding-right: 15px;
        margin: 0;
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

.emptyArray{
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

#genre-music-select{
    width: max-content;
    background-color: $secondaryColor;
    color: white;
    border: none;
    margin-right: 150px;
    height: 50%;
}

</style>