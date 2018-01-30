<template>
    <div>
        <my-header></my-header>
        <div class="index my-container">
            <div class="row">
                <div class="col-8 main">
                    <!--banner-->
                    <div v-swiper:mySwiper="swiperOption" class="banner">
                            <div class="swiper-wrapper">
                                <div class="swiper-slide" v-for="banner in banners">
                                    <img :src="banner">
                                </div>
                            </div>
                            <div class="swiper-pagination swiper-pagination-white"></div>
                            <div class="swiper-button-next swiper-button-white"></div>
                            <div class="swiper-button-prev swiper-button-white"></div>
                        </div>
                    <!--推荐专题-->
                    <div class="recommend-collection">
                        <nuxt-link to="/collection/123">
                            <img src="../static/gushi.jpg" alt="">
                            <span>故事</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../static/renwen.jpg" alt="">
                            <span>人文社科</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../static/shouhui.jpg" alt="">
                            <span>手绘</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../static/wenxue.jpg" alt="">
                            <span>文学</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../static/renwen.jpg" alt="">
                            <span>人文社科</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../static/shouhui.jpg" alt="">
                            <span>手绘</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../static/wenxue.jpg" alt="">
                            <span>文学</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../static/renwen.jpg" alt="">
                            <span>人文社科</span>
                        </nuxt-link>
                        <nuxt-link to="/collectiob/123" class="more-hot-collection">
                            更多热门专题
                            <i class="fa fa-angle-right"></i>
                        </nuxt-link>
                    </div>
                    <div class="split-line"></div>
                    <!--文章列表-->
                    <div id="list-container">
                        <ul class="note-list">
                            <li class="have-img">
                                <!--图片-->
                                <nuxt-link to="/p/123" class="wrap-img">
                                    <img src="../static/pic1.jpg" alt="">
                                </nuxt-link>
                                <!--正文部分-->
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">测试用户</nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <!--标题-->
                                    <nuxt-link to="/p/123" class="title">
                                        如何把书中的知识转化为能力？这是我见过的最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            579
                                        </nuxt-link>
                                        <nuxt-link to="p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li>
                                <!--正文部分-->
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">测试用户</nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <!--标题-->
                                    <nuxt-link to="/p/123" class="title">
                                        如何把书中的知识转化为能力？这是我见过的最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            579
                                        </nuxt-link>
                                        <nuxt-link to="p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li class="have-img">
                                <!--图片-->
                                <nuxt-link to="/p/123" class="wrap-img">
                                    <img src="../static/pic1.jpg" alt="">
                                </nuxt-link>
                                <!--正文部分-->
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">测试用户</nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <!--标题-->
                                    <nuxt-link to="/p/123" class="title">
                                        如何把书中的知识转化为能力？这是我见过的最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            579
                                        </nuxt-link>
                                        <nuxt-link to="p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li>
                                <!--正文部分-->
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">测试用户</nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <!--标题-->
                                    <nuxt-link to="/p/123" class="title">
                                        如何把书中的知识转化为能力？这是我见过的最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">短篇小说</nuxt-link>
                                        <nuxt-link to="/p/123" class="tag">
                                            <i class="fa fa-eye"></i>
                                            579
                                        </nuxt-link>
                                        <nuxt-link to="p/123" class="tag">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            546
                                        </span>
                                    </div>
                                </div>
                            </li>
                        </ul>
                    </div>
                    <!--阅读更多-->
                    <nuxt-link to="/" class="load-more">
                        阅读更多
                    </nuxt-link>
                </div>
                <div class="col-4 aside">
                    <div class="board">
                        <nuxt-link to="/">
                            <img src="../assets/img/1.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/2.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/3.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/4.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/5.png" alt="">
                        </nuxt-link>
                    </div>
                    <!--二维码-->
                    <div class="download">
                        <img src="../static/myself.png">
                        <div>&nbsp;&nbsp;这是我的微信二维码，有问题请加我微信</div>
                    </div>
                    <!--推荐作者-->
                    <div class="recommend-author">
                        <div class="title">
                            <span>推荐作者</span>
                            <a class="page-change"
                               href="javascript:void(0)" @click="rotate">
                                <i class="fa fa-refresh" ref="refresh"></i>
                                换一批
                            </a>
                        </div>
                        <ul class="list">
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../static/gushi.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    占小狼
                                </nuxt-link>
                                <p>
                                    谢了152.9k·7.2k喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../static/gushi.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    占小狼
                                </nuxt-link>
                                <p>
                                    谢了152.9k·7.2k喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../static/gushi.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    占小狼
                                </nuxt-link>
                                <p>
                                    谢了152.9k·7.2k喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../static/gushi.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    占小狼
                                </nuxt-link>
                                <p>
                                    谢了152.9k·7.2k喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../static/gushi.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    占小狼
                                </nuxt-link>
                                <p>
                                    谢了152.9k·7.2k喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../static/gushi.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    占小狼
                                </nuxt-link>
                                <p>
                                    谢了152.9k·7.2k喜欢
                                </p>
                            </li>
                        </ul>
                        <nuxt-link to="/" class="find-more">
                            查看更多
                            <i class="fa fa-angle-right"></i>
                        </nuxt-link>
                    </div>
                </div>
            </div>
        </div>
        <footer class="my-container">
            <div class="row">
                <div class="col-12 footer">
                    <nuxt-link to="/">关于我自己</nuxt-link>
                    <em> · </em>
                    <nuxt-link to="/">联系方式：</nuxt-link>
                    <em> · </em>
                    <nuxt-link to="/">QQ:</nuxt-link>
                    <em> · </em>
                    <nuxt-link to="/">品牌与徽标</nuxt-link>
                    <em> · </em>
                    <nuxt-link to="/">帮助中心</nuxt-link>
                    <em> · </em>
                    <nuxt-link to="/">合作伙伴</nuxt-link>
                </div>
            </div>
        </footer>
    </div>
</template>
<script>
    import myHeader from '~/components/myHeader'
    export default {
        data(){
            return {
                banners:[
                    '/lunbo1.jpg',
                    '/lunbo2.jpg',
                    '/lunbo3.jpg',
                    '/lunbo4.jpg'
                ],
                swiperOption: {
                    loop: true,
                    slidesPerView: 'auto',
                    centeredSlides: true,
                    spaceBetween: 30,
                    autoplay:{
                        delay:3000,//切换时间
                        stopOnLastSlide:false,//是否停止在最后一张
                        disableOnInteraction:false //禁止轮播
                    },
                    pagination: {
                        el: '.swiper-pagination'
                    },
                    navigation:{
                        nextEl:'.swiper-button-next',
                        prevEl:'.swiper-button-prev'
                    },
                    on: {
                        slideChange() {
//                            console.log('onSlideChangeEnd', this);
                        },
                        tap() {
//                            console.log('onTap', this);
                        }
                    }
                },
                deg:360
            }
        },
        components:{
            myHeader
        },
        mounted:{

        },
        methods:{
            rotate:function () {
                this.deg = this.deg + 360
                console.log(this.deg)
                this.$refs.refresh.style.transform = `rotate(${this.deg}deg)`;
            }
        }
    }
</script>
<style>

</style>