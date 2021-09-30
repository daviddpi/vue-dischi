<template>
    
    <option @change="$emit('choose', genre)" value="genre">{{ genre }}</option>
    
</template>

<script>
export default {
    props: {
        genre: String,
    }
}
</script>

<style lang="scss">
@import '../style/general.scss';

</style>