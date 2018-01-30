<template>
    <div>
        <my-header></my-header>
        <div class="note">
            <!--文章区域-->
            <div class="post">
                <!--正文-->
                <div class="article">
                    <h1 class="title">月薪三千，就该去死吗？</h1>
                    <div class="author">
                        <nuxt-link to="/u/123" class="avatar">
                            <img src="../../assets/img/default-avatar.jpg" alt="">
                        </nuxt-link>
                        <div class="info">
                            <span class="name">测试用户</span>
                            <a href="javascript:void(0)" class="follow btn-sm border"
                            @click="isFollow" :class="followObj" @mouseover="noFollow" @mouseleave="beFollow">
                                <i class="fa" :class="iconObj" ref="icon"></i>
                                <span ref="guanzhu">关注</span>
                            </a>
                            <!--<a href="javascript:void(0)" class="follow btn-sm border"-->
                               <!--@click="guanzhu" v-if="show">-->
                                <!--<i class="fa fa-plus-square-o"></i>-->
                                <!--关注-->
                            <!--</a>-->
                            <!--<a href="javascript:void(0)" class="btn-sm border change"-->
                                <!--v-if="!show" @mouseover="change" ref="changes" @mouseleave="leave" @click="guanzhu">√ 已关注-->
                            <!--</a>-->
                            <div class="meta">
                                <span>2018.01.23 16:09</span>
                                <span>字数 2273</span>
                                <span>阅读 882</span>
                                <span>评论 7</span>
                                <span>喜欢 34</span>
                            </div>
                        </div>
                    </div>
                </div>
                <!---->
                <div></div>
            </div>
            <!--悬浮操作框-->
            <div class="side-bar"></div>
            <!--对应得推荐阅读-->
            <div class="note-bottom"></div>
        </div>
    </div>
</template>
<script>
    import myHeader from  '../../components/myHeader.vue'
    export default {
        data(){
            return {
//                show:true
                followObj:{
                    follow:true,
                    following:false
                },
                iconObj:{
                    'fa-plus-square-o':true,
                    'fa-close':false
                }
            }
        },
        components:{
            myHeader
        },
        methods:{
            isFollow:function () {
                this.followObj.follow = !this.followObj.follow
                this.followObj.following = !this.followObj.following
                this.iconObj['fa-plus-square-o'] = !this.iconObj['fa-plus-square-o']
                this.iconObj['fa-close'] = !this.iconObj['fa-close']
                let word = this.$refs.guanzhu.innerHTML
                this.$refs.guanzhu.innerHTML = word == "关注" ? '已关注' :'关注'
            },
            noFollow:function () {
                let word = this.$refs.guanzhu.innerHTML
                if(word == '已关注'){
                    this.$refs.guanzhu.innerHTML = '取消关注';
                    this.$refs.icon.className = 'fa fa-close';
                }
            },
            beFollow:function () {
                let word = this.$refs.guanzhu.innerHTML
                if(word == '取消关注'){
                    this.$refs.guanzhu.innerHTML = '已关注';
                    this.$refs.icon.className = 'fa fa-check';
                }
            }
//            guanzhu:function () {
//                this.show = !this.show
//            },
//            change:function() {
//                this.$refs.changes.innerText = '× 取消关注'
//            },
//            leave:function () {
//                this.$refs.changes.innerText = '√ 已关注'
//            }
        }
    }
</script>