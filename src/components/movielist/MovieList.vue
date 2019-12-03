<template>
    <div class="bScroll">
        <div v-if="movieList.length">
            <MovieItem
                v-for="movie in movieList"
                :key="movie.id"
                :movie="movie"
                
            ></MovieItem>
        </div>
        <van-loading type="spinner" color="#1989fa" v-else />   
    </div>
</template>

<script>
import Vue from 'vue';
import BScroll from 'better-scroll';
import { get } from "utils/http"
import MovieItem from "./MovieItem"

import {Loading} from 'vant';
import { PullRefresh } from 'vant'
Vue.use(Loading);

export default {
    data(){
        return {
            movieList:[],
            isLoading: false,
            count: 0
        }
    },

    components:{
        MovieItem
    },

    async created() {

        
        let result = await get({
            url:"/ajax/movieOnInfoList?token="
        })

        this.movieList = result.movieList

        new BScroll(".bScroll",{
            pullUpLoad: true,
            click: true
        })
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
.van-loading{
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    width: .41rem;
    height: .41rem;
}
.bScroll{
    width: 100%;
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