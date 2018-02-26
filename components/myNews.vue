<template>
    <div>
        <div class="drop-menu">
            <ul>
                <li class="">
                    <nuxt-link to="/o/review" active-class="active">
                        <i class="fa fa-comment-o"></i>
                        <span>评论</span>
                    </nuxt-link>
                </li>
                <li class="">
                    <nuxt-link to="/o/jianxin" active-class="active">
                        <i class="fa fa-envelope-open-o"></i>
                        <span>简信</span>
                    </nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/o/submit" active-class="active">
                        <i class="fa fa-upload"></i>
                        投稿请求
                    </nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/o/zan" active-class="active">
                        <i class="fa fa-heart-o"></i>
                        <span>喜欢和赞</span>
                    </nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/o/attention" active-class="active">
                        <i class="fa fa-user-o"></i>
                        <span>关注</span>
                    </nuxt-link>
                </li>
            </ul>
        </div>
    </div>
</template>
<style scoped>
    .drop-menu{
        position: fixed;
        top:0;
        width: 280px;
        margin-top: 86px;
        background-color: #fff;
        padding-bottom: 30px;
    }
    .drop-menu ul{
        padding: 10px 0;
        margin: 0 0 10px 0;
    }
    .drop-menu ul li a.active {
        background-color: #f0f0f0;
        border-right: 4px;
    }
    .drop-menu a:hover{
        background-color: #f0f0f0;
        border-radius: 4px;
    }
    .drop-menu ul li a{
        height:auto;
        line-height: 30px;
        padding: 10px 25px;
        display: block;
    }
    .drop-menu ul li a:hover{
        background-color: #f5f5f5;
    }
    .drop-menu ul li a i{
        margin-right: 15px;
        color: #ea6f5a;
        font-size: 24px;
        vertical-align: middle;
    }
    .drop-menu ul li a span{
        font-size: 15px;
        vertical-align: middle;
    }
</style>
<script>
    export default{
        name:'myNews',
        data(){},
        methods:{

        }
    }
</script>