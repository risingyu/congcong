<template>
    <div id="detailContainer" class="slide-enter-active">
        <Header title="影片详情" > 
            <i class="iconfont icon-arrow_left" @touchstart="handleToBack"></i>
        </Header>
        <Loading v-if="isLoading" />
        <div v-else id="content" class="contentDetail">
            <div class="detail_list">
                <div class="detail_list_bg"></div>
                <div class="detail_list_filter"></div>
                <div class="detail_list_content">
                    <div class="detail_list_img">
                        <img :src="detailMovie.img | setWH('148.208')" alt="">
                    </div>
                    <div class="detail_list_info">
                        <h2>{{ detailMovie.nm }}</h2>
                        <p>{{ detailMovie.enm }}</p>
                        <p>{{ detailMovie.sc }}</p>
                        <p>{{ detailMovie.cat }}</p>
                        <p>{{ detailMovie.src }}</p>
                        <p>{{ detailMovie.pubDesc }}</p>
                    </div>
                </div>
            </div>
            <div class="detail_intro">
                <p>{{ detailMovie.dra }}</p>
            </div>
            <div class="detail_player swiper-container" ref="detail_player">
                <ul class="swiper-wrapper">
                    <li v-for="(item,index) in detailMovie.photos" :key="index" class="swiper-slide">
                        <div>
                            <img :src="item | setWH('140.127')" alt="">
                        </div>
                    </li>
                </ul>
            </div>

            <!-- <div class="detail_list">
                <div class="detail_list_bg"></div>
                <div class="detail_list_filter"></div>
                <div class="detail_list_content">
                    <div class="detail_list_img">
                        <img src="/images/movie_1.jpg" alt="">
                    </div>
                    <div class="detail_list_info">
                        <h2>蜘蛛侠：英雄远征</h2>
                        <p>Spider-Man:Far From Home</p>
                        <p>9.0</p>
                        <p>动作 / 冒险 / 科幻</p>
                        <p>美国 / 127分钟</p>
                        <p>2019-06-28中国大陆上映</p>
                    </div>
                </div>
            </div>
            <div class="detail_intro">
                <p>2019漫威宇宙最新力作《蜘蛛侠：英雄远征》6月28日提前北美4天上映，领跑2019暑期档！
                    故事全面延续“复联4”，蜘蛛侠志承钢铁侠远征欧洲，独挑大梁对抗群敌！新角色“神秘客”
                    穿越多元宇宙霸气登场！神盾局局长尼克·弗瑞回归领军！“漫威新铁三角”组合强势出击！
                    全新蜘蛛战衣酷炫升级！史诗对决燃爆今夏突破想象极限！</p>
            </div>
            <div class="detail_player swiper-container">
                <ul class="swiper-wrapper">
                    <li class="swiper-slide">
                        <div>
                            <img src="/images/person_1.jpg" alt="">
                        </div>
                        <p>汤姆·赫兰德</p>
                        <p>蜘蛛侠</p>
                    </li>
                </ul>
            </div> -->
        </div>
    </div>
</template>

<script>

import Header from '@/components/Header';

export default {
    name : 'Detail',
    data(){
        return{
            detailMovie : {},
            isLoading : true
        }
    },
    components : {
        Header
    },
    props : ['movieId'],
    methods : {
        handleToBack(){
            this.$router.back();
        }
    },
    mounted(){
        //console.log( this.movieId );
        this.axios.get('/api/detailmovie?movieId=' + this.movieId).then((res)=>{
            var msg = res.data.msg;
            if ( msg === 'ok') {
                this.detailMovie = res.data.data.detailMovie;
                /* setTimeout(() => {
                    this.isLoading = false;
                }, 2000); */
                this.isLoading = false;
                this.$nextTick(()=>{
                    new Swiper(this.$refs.detail_player, {
                        slidesPerView : 'auto',
                        freeMode : true,
                        freeModeSticky: true
                    });
                });
            }
        });
    }
}
</script>

<style scoped>
#detailContainer{ position: absolute; left: 0; top: 0; z-index: 100; width: 100%; min-height: 100%; background: white;}
#detailContainer.slide-enter-active{ animation: .3s slideMove;}
@keyframes slideMove{
    0%{ transform : translateX(100%); }
    100%{ transform : translateX(0); }
}
#content.contentDetail{ display: block; margin-bottom: 0;}
#content .detail_list{ height: 200px; width: 100%; position: relative; overflow: hidden;}
.detail_list .detail_list_bg{ width: 100%; height: 100%; background: url(/images/movie_1.jpg) 0 40%; filter: blur(20px); /* background: */ }
.detail_list .detail_list_filter{ width: 100%; height: 100%; position: absolute; background-color: #40454d; opacity: .55; /* position: */ }
.detail_list .detail_list_content{ display: flex; width: 100%; height: 100%; position: absolute; left: 0; top: 0; z-index: 2;}
.detail_list .detail_list_img{ width: 108px; height: 150px; border: solid 1px #f0f2f3; margin: 20px;}
.detail_list .detail_list_img img{ width: 100%; height: 100%;}
.detail_list .detail_list_info{ margin-top: 20px;}
.detail_list .detail_list_info h2{ font-size: 20px; color: white; font-weight: normal; line-height: 40px;}
.detail_list .detail_list_info p{ color: white; line-height: 20px; font-size: 14px; color: #ccc;}

#content .detail_intro{ padding: 10px};
#content .detail_player{ margin: 20px;}
.detail_player .swiper-slide{ width: 70px; margin-right: 20px; text-align: center; font-size: 14px;}
.detail_player .swiper-slide img{ width: 100%; margin-bottom: 5px;}
.detail_player .swiper-slide p:nth-of-type(2){ color: #999;}
</style>
