<template>
    <div class="movie-wrap">
        <header>猫眼电影</header>
        <Ad></Ad>
        <nav class="topbar">
            <div class="city-entry">
                <span>北京</span>
                <i class="yo-ico">&#xf033;</i>
            </div>
            <div class="swich-hot">
                <ul>
                    <router-link to="/index/movies/intheaters" tag="li" active-class="active">正在热映</router-link>
                <router-link :to="{path:'/index/movies/comingsoon'}" tag="li" active-class="active">即将上映</router-link >
                </ul>
            </div>
            <div class="btn-search yo-ico">&#xf067;</div>
        </nav>

        <router-view></router-view>
    </div>
</template>

<script>
    import MovieList from 'components/movielist/MovieList';
    import Ad from "./Ad"
    export default {
        components:{
            MovieList,
            Ad
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
        header {
            height: 0.44rem;
            text-align: center;
            line-height: 0.44rem;
            color: #ffffff;
            font-size: 0.18rem;
            font-weight: 400;
            background: #e54847;
        }

        nav {
            height: 0.44rem;
            display: flex

            >div:first-child {
                flex: 16;
                padding-left: 0.15rem;
                font-size: 0.16rem;
                display: flex;
                align-items: center;
                color: #666;
            }

            >div:nth-child(2) {
                flex: 43;

                ul {
                    display: flex;
                    width: 100%;
                    height: 100%;

                    li {
                        line-height: 0.42rem;
                        text-align: center;
                        color: #666;
                        flex: 1;
                        font-weight: 900;
                        margin: 0 0.05rem;
                        &.active {
                            color: #e54847;
                            border-bottom: 0.02rem solid #e54847;
                        }
                    }
                }
            }

            >div:last-child {
                flex: 16;
                padding-right: 0.15rem;
                padding-left: 0.1rem;
                line-height: 0.44rem;
                text-align: right;
                font-size: 0.18rem;
                color: #e54847;
            }
        }
    
</style>