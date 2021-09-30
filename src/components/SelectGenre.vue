<template>
    <select id="genre-music-select" v-model="genre" @change="$emit('choose', genre)">
        <option value=""> - </option>
        <option v-for="(element, index) in genreList" :key="index" :value="element">{{ element }}</option>
    </select> 
</template>

<script>
export default {
    props: {
        genreList: Array,
    },

    data(){
        return{
            genre: "",
        }
    }
}
</script>

<style lang="scss">
@import '../style/general.scss';

#genre-music-select{
    width: max-content;
    background-color: $secondaryColor;
    color: white;
    border: none;
    margin-right: 150px;
    height: 50%;
}


</style>