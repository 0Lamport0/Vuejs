<template>
    <div class="bScroll">
        <div>
            <MovieItem
                v-for="movie in movieList"
                :key="movie.id"
                :movie="movie"
            ></MovieItem>
        </div>
    </div>
</template>

<script>
import bScroll from 'better-scroll';
import { get } from "utils/http"
import MovieItem from "./MovieItem"

export default {
    data(){
        return {
            movieList:[]
        }
    },

    components:{
        MovieItem
    },

    async mounted() {

        
        let result = await get({
            url:"/ajax/movieOnInfoList?token="
        })

        this.movieList = result.movieList

        new bScroll(".bScroll")
    }
}
</script>

<style lang="stylus">
header{
	height: 44px;
	background: #e54847;
	color: #FFFFFF;
	text-align: center;
	line-height: 44px;
	font-size: 18px;
}
.bScroll{
    width: 100%;
    overflow-y: scroll;
}
    .page{
        position stacic !important    
    }
    section {
        flex: 1;
        position: static !important;
        .main-block{
            padding-right: .16rem;
        }
        .tab-content .list-wrap .item .content-wrapper{
            height: 1.16rem;
            max-height: 1.16rem;
        }
        .page-wrap{
            height: 100%;
            // position:static !important;
            .tab-block{
                height:100%;
                .tab-content{
                    height:100%;
                    overflow-y:scroll;
                }
            }
        }
    }
</style>