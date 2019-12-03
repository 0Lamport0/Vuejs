<template>
    <div class="movie-wrap">
        <router-view></router-view>
    </div>
</template>

<script>
    import MovieList from 'components/movielist/MovieList';
    export default {
        components:{
            MovieList
        }
    };
</script>

<style lang="stylus" scoped>
    @import '~assets/stylus/border.styl';

    .movie-wrap {
        display: flex;
        width: 100%;
        height: 100%;
        flex-direction: column;
    }
       
    
</style>