<template>
    <div>
        <div id="comment-list" class="comment-list">
            <!--提交的表单-->
            <form action="" class="new-comment">
                <nuxt-link to="/u/123" class="avatar">
                    <img src="../assets/img/default-avatar.jpg" alt="">
                </nuxt-link>
                <textarea placeholder="写下你的评论" v-model="value" @focus="send=true"></textarea>
                <transition enter-active-class="animated fadeIn" leave-active-class="animated fadeOut" :duration="500">
                    <div class="write-function-block clearfix" v-if="send">
                        <div class="emoji-modal-wrap">
                            <a href="javascript:void(0)" class="emoji" @click="showEmoji = !showEmoji">
                                <i class="fa fa-smile-o"></i>
                            </a>
                            <transition :duration="200" enter-active-class="animate fadeIn"
                            leaver-active-class="animate fadeOut">
                                <!--表情-->
                                <div v-if="showEmoji" class="emoji-modal arrow-up">
                                    <vue-emoji @select="selectEmoji">

                                    </vue-emoji>
                                </div>
                            </transition>
                        </div>
                        <div class="hint">
                            Ctrl+Enter 发表
                        </div>
                        <a href="javascript:void(0)" @click="sendData" class="btn btn-send">发送</a>
                        <a href="javascript:void(0)" class="cancel" @click="send=false">取消</a>
                    </div>
                </transition>
            </form>
            <!--留言的列表-->
            <div id="normal-comment-list" class="normal-comment-list">
                <!--留言排序-->
                <div class="top-title">
                    <span>25条评论</span>
                    <a class="author-only" href="javascript:void (0)">只看作者</a>
                    <div class="pull-right">
                        <a href="javascript:void(0)" class="active">按喜欢排序</a>
                        <a href="javascript:void(0)">按时间正序</a>
                        <a href="javascript:void(0)">按时间倒序</a>
                    </div>
                </div>
                <!--留言正文-->
                <div class="comment-placeholder" style="display: none">
                    <div class="author">
                        <div class="avatar">
                            <!--<img src="../assets/img/default-avatar.jpg" alt="">-->
                        </div>
                        <div class="info">
                            <div class="name"></div>
                            <div class="meta"></div>
                        </div>
                    </div>
                    <div class="title"></div>
                    <div class="title animated-delay"></div>
                    <div class="tool-group">
                        <i class="fa fa-thumbs-up"></i>
                        <div class="zan"></div>
                        <i class="fa fa-comment"></i>
                        <div class="like"></div>
                    </div>
                </div>
                <div v-for="(comment,index) in comments" class="comment" :id="'comment-'+comment.id">
                    <div class="comment-content">
                        <div class="author">
                            <!--<div class="v-tooltop-content">-->
                                <nuxt-link class="avatar" to="/u/123">
                                    <img :src="comment.user.avatar" alt="">
                                </nuxt-link>
                            <!--</div>-->
                            <div class="info">
                                <nuxt-link to="/u/123" class="name">
                                    {{comment.user.nickname}}
                                </nuxt-link>
                                <div class="meta">
                                    <span>
                                        {{comment.floor}}楼.
                                        {{comment.create_at | formatDate}}
                                    </span>
                                </div>
                            </div>
                        </div>
                        <div class="comment-wrap">
                            <p>{{comment.compiled_content}}</p>
                            <div class="tool-group">
                                <a href="javascript:void(0)">
                                    <i class="fa fa-thumbs-o-up"></i>
                                    <span>{{comment.like_count}}人点赞</span>
                                </a>
                                <a href="javascript:void(0)">
                                    <i class="fa fa-comment-o"></i>
                                    <span @click="reply(index)">回复</span>
                                </a>
                            </div>
                        </div>
                    </div>
                    <!--二级回复-->
                    <div class="sub-comment-list" v-if="comment.children.length != 0">
                        <div :id="'comment-'+subComment.id" v-for="(subComment,index) in comment.children" class="sub-comment">
                            <p>
                                <nuxt-link to="/u/123" class="abc">
                                    {{subComment.user.nickname}}:
                                </nuxt-link>
                                <span v-html="subComment.compiled_content"></span>
                            </p>
                            <div class="sub-tool-group">
                                <span>{{subComment.create_at | formatDate}}</span>
                                <a href="javascript:void(0)">
                                    <i class="fa fa-comment-o"></i>
                                    <span @click="replys(index)">回复</span>
                                </a>
                            </div>
                        </div>
                        <div class="more-comment">
                            <a href="javascript:void(0)" class="add-comment-btn" @click="showSubCommentForm(index)">
                                <i class="fa fa-pancil"></i>
                                <span >添加新评论</span>
                            </a>
                        </div>
                        <transition enter-active-class="animated fadeIn" leave-active-class="animated fadeOut" :duration="500">
                            <form v-if="activeIndex.includes(index)">
                            <textarea placeholder="写下你的评论"></textarea>
                                <div class="write-function-block clearfix">
                                    <div class="emoji-modal-wrap">
                                        <a href="javascript:void(0)" class="emoji" @click="showSubEmoji(index)">
                                            <i class="fa fa-smile-o"></i>
                                        </a>
                                        <transition :duration="200" enter-active-class="animate fadeIn"
                                                    leaver-active-class="animate fadeOut">
                                            <!--表情-->
                                            <div v-if="emojiIndex.includes(index)" class="emoji-modal arrow-up">
                                                <vue-emoji @select="selectSubEmoji" :index="index">

                                                </vue-emoji>
                                            </div>
                                        </transition>
                                    </div>
                                    <div class="hint">
                                        Ctrl+Enter 发表
                                    </div>
                                    <a href="javascript:void(0)" @click="sendSubCommentData" class="btn btn-send">发送</a>
                                    <a href="javascript:void(0)" class="cancel" @click="closeSubComment(index)">取消</a>
                                </div>
                        </form>
                        </transition>
                    </div>
                    <!--显示表单-->
                </div>
            </div>
        </div>
    </div>
</template>
<style>
    .form{
        display: none;
    }
    .fade-enter-active,.fade-leave-active {
        opacity: 1;
        transition: .3s;
        -webkit-transition: .3s
    }
    .fade-enter,.fade-leave-to {
        opacity: 0;
        transform: translate3d(0,-5%,0);
        -webkit-transform: translate3d(0,-5%,0);
        transition: .3s;
        -webkit-transition: .3s
    }
    .note .post .comment-list {
        padding-top: 20px;
    }
    .note .post .comment-list .new-comment {
        position: relative;
        margin-left: 48px;
        margin-bottom: 20px;
    }
    .note .post .comment-list .avatar{
        width: 38px;
        height: 38px;
        display: inline-block;
        margin-right: 5px;
    }
    .note .post .comment-list .new-comment .avatar {
        position: absolute;
        left: -48px;
    }
    .note .post .comment-list textarea {
        width: 100%;
        height: 80px;
        padding: 10px 15px;
        border: 1px solid #ccc;
        border-radius: 4px;
        display: inline-block;
        vertical-align: top;
        outline-style: none;
        resize: none;
        font-size: 13px;
        background-color: #f8f8f8;
    }
    .note .post .comment-list .emoji-modal-wrap {
        position: relative;
    }
    .note .post .comment-list .emoji{
        float: left;
        margin-top: 14px;
    }
    .note .post .comment-list .emoji i{
        font-size: 25px;
        color: #969696;
    }
    .note .post .comment-list .emoji i:hover{
        color: #333;
    }
    .note .post .comment-list .hint {
        float: left;
        margin: 20px 0 0 20px;
        font-size: 13px;
        color: #969696;
    }
    .note .post .comment-list .cancel{
        float: right;
        font-size: 16px;
        margin: 18px 30px 0 0;
        color: #969696!important;
    }
    .note .post .comment-list .cancel:hover{
        color: #333!important;
    }
    .note .post .comment-list .btn-send{
        float: right;
        width: 78px;
        padding: 8px 18px;
        margin: 10px 0;
        font-size: 18px;
        background-color: #42c020;
        border-radius: 20px;
        color: #fff!important;
        box-shadow: #3db922;
    }
    .note .post .comment-list .btn-send:hover{
        background-color: #3db922;
    }
    .note .post .comment-list .emoji-modal-wrap .emoji-modal{
        position: absolute;
        top: 50px;
        left: -48px;
        width: 402px;
        height: 208px;
        padding: 10px;
        background-color: #fff;
        border: 1px solid #d9d9d9;
        border-radius: 4px;
        box-shadow: 0 5px 25px rgba(0,0,0,0.1);
    }
    .note .post .comment-list .emoji-modal-wrap .arrow-up:after{
        content: '';
        display: inline-block;
        position: absolute;
        left: 48px;
        top: -15px;
        width: 15px;
        height: 15px;
        border-left: 1px solid #d9d9d9;
        border-top: 1px solid #d9d9d9;
        background-color: #fff;
        transform: translate3d(0,50%,0) rotate(45deg);
    }
    .note .post .comment-list .normal-comment-list{
        margin-top: 30px;
    }
    .note .post .comment-list .normal-comment-list .top-title{
        padding-bottom: 20px;
        border-bottom: 1px solid #f0f0f0;
    }
    .note .post .comment-list .normal-comment-list .top-title span{
        font-size: 17px;
        font-weight: 700;
    }
    .note .post .comment-list .normal-comment-list .top-title .author-only{
        padding: 4px 8px;
        font-size: 12px;
        border: 1px solid #e0e0e0;
        border-radius: 12px;
        color: #969696!important;
        margin-left: 10px;
    }
    .note .post .comment-list .normal-comment-list .top-title .pull-right a{
        margin-left: 10px;
        font-size: 12px;
        color: #969696!important;
    }
    .note .post .comment-list .normal-comment-list .top-title .pull-right a.active{
        color: #2f2f2f!important;
    }
    /*.note .post .comment-list .normal-comment-list .top-title .pull-right a:hover{*/
        /*color: #2f2f2f!important;*/
    /*}*/
    .comment-placeholder{
        padding: 20px 0 30px 0;
    }
    .comment-placeholder .author{
        margin-bottom: 15px;
    }
    .comment-placeholder .avatar {
        width: 38px;
        height: 38px;
        background-color: #eaeaea;
        border-radius: 50%;
    }
    .comment-placeholder .author .info{
        display: inline-block;
    }
    .comment-placeholder .author .info .name{
        width: 60px;
        height: 15px;
        margin-bottom: 6px;
    }
    .comment-placeholder .author .info .meta{
        background-color: #eaeaea;
        width: 120px;
        height: 12px;
    }
    .comment-placeholder .title{
        width: 100%;
        height: 16px;
        background-color: #eaeaea;
        margin-bottom: 8px;
        animation: loading 1s ease-in-out infinite;
    }
    .comment-placeholder .animated-delay{
        animation: loading 1s ease-in-out -.5s infinite;
    }
    @keyframes loading {
        0%{
            width: 60%;
        }
        50%{
            width: 100%;
        }
        100%{
            width: 60%;
        }
    }
    .comment-placeholder .tool-group{
        font-size: 15px;
        color: #eaeaea;
        padding-top: 5px;
    }
    .comment-placeholder .tool-group i{
        margin-right: 5px;
    }
    .comment-placeholder .tool-group .zan{
        width: 40px;
        height: 14px;
        margin-right: 10px;
        display: inline-block;
        background-color: #eaeaea;
    }
    .note .post .comment-list .comment{
        padding: 20px 0 30px 0;
        border-bottom: 1px solid #f0f0f0;
    }
    .note .post .comment-list .info{
        display: inline-block;
        vertical-align: middle;
    }
    .note .post .comment-list .info .name {
        font-size: 15px;
    }
    .note .post .comment-list .info .meta{
        font-size: 12px;
        color: #969696;
    }
    .note .post .comment-list .comment p{
        font-size: 16px;
        margin: 10px 0;
        line-height: 1.5;
        word-break: break-word!important;
    }
    .note .post .comment-list .comment .tool-group a{
        color: #969696!important;
        margin-right: 10px;
    }
    .note .post .comment-list .comment .tool-group a i{
        font-size: 18px;
        margin-right: 5px;
    }
    .note .post .comment-list .comment .tool-group a span{
        font-size: 14px;
    }
    .note .post .comment-list .sub-comment-list{
        padding-left: 20px;
        margin: 20px;
        border-left: 2px solid #d9d9d9;
    }
    .note .post .comment-list .sub-comment {
        padding-bottom: 15px;
        margin-bottom: 15px;
        border-bottom: 1px dashed #f0f0f0;
    }
    .note .post .comment-list .sub-comment p{
        font-size: 14px;
        line-height: 1.5;
        margin-bottom: 5px;
    }
    .note .post .comment-list .sub-comment p a{
        color: #3194d0!important;
    }
    .note .post .comment-list .sub-comment .sub-tool-group {
        font-size: 12px;
        color: #969696;
    }
    .note .post .comment-list .sub-comment .sub-tool-group a{
        margin-left: 10px;
    }
    .note .post .comment-list .sub-comment .sub-tool-group a i{
        margin-right: 5px;
    }
    .note .post .comment-list .more-comment {
        margin-bottom: 30px;
        font-size: 14px;
        color: #969696;
    }
    .note .post .comment-list .more-comment a:hover{
        color: #333;
    }
    .note .post .comment-list .more-comment i{
        margin-right: 5px;
    }
</style>
<script>
    import vueEmoji from '~/components/vueEmoji.vue'
    export default {
        name:'myComment',
        data(){
            return{
                send:false,
                showEmoji:false,
                value:'',
                send_one:true,
                activeIndex:[],
                emojiIndex:[],
                comments:[
                    {
                        id:19935725,
                        floor:2,
                        liked:true,
                        like_count:66,
                        note_id:23054702,
                        user_id:6780849,
                        user:{
                            avatar:'/default-avatar.jpg',
                            id:6780849,
                            is_author:false,
                            nickname:'七岁就很拽',
                            slug:'7edb3d2d9c7c'
                        },
                        create_at:'2018-01-25T09:40:18.000+08:00',
                        children_count:4,
                        compiled_content:'今年25岁的我，年纪轻轻月薪就已经达到2800了，加上提成满勤再加上我天生的睿智头脑，平常帮客人拿下拖鞋点下烟得点小费可以拿到3100。觉得自己这几年过得也不容易，现在这么有钱，都不知道怎么花了，开始花钱大手大脚了，以前网吧包夜都是喝自来水，现在敢喝红茶了，还是一晚上买两瓶，甚至打电话出去叫炒河粉而且还要加个鸡蛋，我觉得现在有点迷失自我，有什么办法？希望能回到初心！',
                        children:[
                            {
                                id:20116365,
                                user_id:2604707,
                                user:{
                                    id:2604707,
                                    nickname:'Bowman',
                                    slug: '60c3849cb847'
                                },
                                parent_id:19935725,
                                create_at:'2018-01-30T14:25:32.000+08:00',
                                compiled_content:'兄die,我也和你有着一样的困惑，甚至一度迷失自我...',
                            },
                            {
                                id:20122216,
                                user_id:9933465,
                                user:{
                                    id:9933465,
                                    nickname:'美女荷官',
                                    slug: '2fd904a45f5f'
                                },
                                parent_id:19935725,
                                create_at:'2018-01-25T09:40:18.000+08:00',
                                compiled_content:'是你李大钊飘了,还是我陈独秀拿不动刀了',
                            },
                            {
                                id:20122226,
                                user_id:9964877,
                                user:{
                                    id:9964877,
                                    nickname:'保坤文化传媒',
                                    slug: 'eca4b8eed92d'
                                },
                                parent_id:19935725,
                                create_at:'2018-01-30T14:25:49.000+08:00',
                                compiled_content:'哈哈。。',
                            }
                        ],
                    },
                    {
                        id:19935796,
                        floor:3,
                        liked:false,
                        like_count:66,
                        note_id:23054702,
                        user_id:6780849,
                        user:{
                            avatar:'/default-avatar.jpg',
                            id:6780849,
                            is_author:false,
                            nickname:'八岁就很拽',
                            slug:'7edb3d2d9c7c'
                        },
                        create_at:'2018-01-25T09:40:18.000+08:00',
                        children_count:4,
                        compiled_content:'作为一名混凝土方块移动工程师，我一直以3000的月薪骄傲，甚至一度迷失自我。。。看了楼主这篇文章，我找回了初心',
                        children:[
                            {
                                id:19949215,
                                user_id:5954136,
                                user:{
                                    id:5954136,
                                    nickname:'与笑颜开',
                                    slug: '88ad9c9678a6'
                                },
                                parent_id:19935796,
                                create_at:'2018-01-25T16:55:40.000+08:00',
                                compiled_content:'混凝土方块移动工程师是啥子工作，我咋没听过？我也做过混凝土这行',
                            },
                            {
                                id:20062029,
                                user_id:8914781,
                                user:{
                                    id:8914781,
                                    nickname:'向天再借5厘米',
                                    slug: '2a62f743574c'
                                },
                                parent_id:19935796,
                                create_at:'2018-01-28T21:06:14.000+08:00',
                                compiled_content:'<a href="/users/88ad9c9678a6" class="maleskine-author" target="_blank" data-user-slug="88ad9c9678a6">@与笑颜开</a> 搬砖',
                            },
                            {
                                id:20122231,
                                user_id:9964877,
                                user:{
                                    id:9964877,
                                    nickname:'保坤文化传媒',
                                    slug: 'eca4b8eed92d'
                                },
                                parent_id:19935796,
                                create_at:'2018-01-30T14:26:00.000+08:00',
                                compiled_content:'好有意思。',
                            }
                        ],
                    },
                    {
                        id:19935725,
                        floor:4,
                        liked:true,
                        like_count:66,
                        note_id:23054702,
                        user_id:6780849,
                        user:{
                            avatar:'/default-avatar.jpg',
                            id:6780849,
                            is_author:false,
                            nickname:'七岁就很拽',
                            slug:'7edb3d2d9c7c'
                        },
                        create_at:'2018-01-25T09:40:18.000+08:00',
                        children_count:4,
                        compiled_content:'今年25岁的我，年纪轻轻月薪就已经达到2800了，加上提成满勤再加上我天生的睿智头脑，平常帮客人拿下拖鞋点下烟得点小费可以拿到3100。觉得自己这几年过得也不容易，现在这么有钱，都不知道怎么花了，开始花钱大手大脚了，以前网吧包夜都是喝自来水，现在敢喝红茶了，还是一晚上买两瓶，甚至打电话出去叫炒河粉而且还要加个鸡蛋，我觉得现在有点迷失自我，有什么办法？希望能回到初心！',
                        children:[
                            {
                                id:20116365,
                                user_id:2604707,
                                user:{
                                    id:2604707,
                                    nickname:'Bowman',
                                    slug: '60c3849cb847'
                                },
                                parent_id:19935725,
                                create_at:'2018-01-30T14:25:32.000+08:00',
                                compiled_content:'兄die,我也和你有着一样的困惑，甚至一度迷失自我...',
                            },
                            {
                                id:20122216,
                                user_id:9933465,
                                user:{
                                    id:9933465,
                                    nickname:'美女荷官',
                                    slug: '2fd904a45f5f'
                                },
                                parent_id:19935725,
                                create_at:'2018-01-25T09:40:18.000+08:00',
                                compiled_content:'是你李大钊飘了,还是我陈独秀拿不动刀了',
                            },
                            {
                                id:20122226,
                                user_id:9964877,
                                user:{
                                    id:9964877,
                                    nickname:'保坤文化传媒',
                                    slug: 'eca4b8eed92d'
                                },
                                parent_id:19935725,
                                create_at:'2018-01-30T14:25:49.000+08:00',
                                compiled_content:'哈哈。。',
                            }
                        ],
                    },
                    {
                        id:19935796,
                        floor:5,
                        liked:false,
                        like_count:66,
                        note_id:23054702,
                        user_id:6780849,
                        user:{
                            avatar:'/default-avatar.jpg',
                            id:6780849,
                            is_author:false,
                            nickname:'二十岁的更拽',
                            slug:'7edb3d2d9c7c'
                        },
                        create_at:'2018-01-25T09:40:18.000+08:00',
                        children_count:4,
                        compiled_content:'作为一名混凝土方块移动工程师，我一直以3000的月薪骄傲，甚至一度迷失自我。。。看了楼主这篇文章，我找回了初心',
                        children:[
                            {
                                id:19949215,
                                user_id:5954136,
                                user:{
                                    id:5954136,
                                    nickname:'与笑颜开',
                                    slug: '88ad9c9678a6'
                                },
                                parent_id:19935796,
                                create_at:'2018-01-25T16:55:40.000+08:00',
                                compiled_content:'混凝土方块移动工程师是啥子工作，我咋没听过？我也做过混凝土这行',
                            },
                            {
                                id:20062029,
                                user_id:8914781,
                                user:{
                                    id:8914781,
                                    nickname:'向天再借5厘米',
                                    slug: '2a62f743574c'
                                },
                                parent_id:19935796,
                                create_at:'2018-01-28T21:06:14.000+08:00',
                                compiled_content:'<a href="/users/88ad9c9678a6" class="maleskine-author" target="_blank" data-user-slug="88ad9c9678a6">@与笑颜开</a> 搬砖',
                            },
                            {
                                id:20122231,
                                user_id:9964877,
                                user:{
                                    id:9964877,
                                    nickname:'保坤文化传媒',
                                    slug: 'eca4b8eed92d'
                                },
                                parent_id:19935796,
                                create_at:'2018-01-30T14:26:00.000+08:00',
                                compiled_content:'好有意思。',
                            }
                        ],
                    }
                ]
            }
        },
        components:{
            vueEmoji
        },
        methods:{
            selectEmoji:function (code) {
                this.showEmoji = false;
                this.value += code;
            },
            sendData:function () {
                console.log('发送value值的数据给后端');
            },
            showSubCommentForm:function (value) {
                if(this.activeIndex.includes(value)){
                    let index = this.activeIndex.indexOf(value);
                    this.activeIndex.splice(index,1)
                }else {
                    this.activeIndex.push(value)
                }
            },
            sendSubCommentData:function (value) {
                let index = this.activeIndex.indexOf(value);
                this.activeIndex.splice(index,1)
            },
            closeSubComment:function (value) {
                let index = this.activeIndex.indexOf(value);
                this.activeIndex.splice(index,1)
            },
            showSubEmoji:function (value) {
                if(this.emojiIndex.includes(value)){
                    let index = this.emojiIndex.indexOf(value)
                    this.emojiIndex.splice(index,1)
                }else {
                    this.emojiIndex.push(value)
                }
            },
            selectSubEmoji:function (value) {
                
            }
        },

    }
</script>