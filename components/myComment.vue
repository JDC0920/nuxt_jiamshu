<template>
    <div>
        <div id="comment-list" class="comment-list">
            <!--提交的表单-->
            <form action="" class="new-comment">
                <nuxt-link to="/u/123" class="avatar">
                    <img src="../assets/img/default-avatar.jpg" alt="">
                </nuxt-link>
                <textarea placeholder="写下你的评论" @focus="send_one=true"></textarea>
                <transition enter-active-class="animated fadeIn" leave-active-class="animated fadeOut" :duration="500">
                    <div class="write-function-block clearfix" v-if="send_one">
                        <div class="emoji-modal-wrap">
                            <a href="javascript:void(0)" class="emoji" @click="showEmoji = !showEmoji" @blur="showEmoji= false">
                                <i class="fa fa-smile-o"></i>
                            </a>
                            <transition :duration="200" enter-active-class="animate fadeIn"
                            leaver-active-class="animate fadeOut">
                                <div v-if="showEmoji" class="emoji-modal arrow-up">

                                </div>
                            </transition>
                        </div>
                        <div class="hint">
                            Ctrl+Enter 发表
                        </div>
                        <a href="javascript:void(0)" class="btn btn-send">发送</a>
                        <a href="javascript:void(0)" class="cancel" @click="send_one=false">取消</a>
                    </div>
                </transition>

            </form>
        </div>
    </div>
</template>
<style>
    .note .post .comment-list {
        padding-top: 20px;
        margin-bottom: 200px;
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
    .note .post .comment-list .new-comment textarea {
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
    .note .post .comment-list .new-comment .emoji-modal-wrap {
        position: relative;
    }
    .note .post .comment-list .new-comment .emoji{
        float: left;
        margin-top: 14px;
    }
    .note .post .comment-list .new-comment .emoji i{
        font-size: 25px;
        color: #969696;
    }
    .note .post .comment-list .new-comment .emoji i:hover{
        color: #333;
    }
    .note .post .comment-list .new-comment .hint {
        float: left;
        margin: 20px 0 0 20px;
        font-size: 13px;
        color: #969696;
    }
    .note .post .comment-list .new-comment .cancel{
        float: right;
        font-size: 16px;
        margin: 18px 30px 0 0;
        color: #969696!important;
    }
    .note .post .comment-list .new-comment .cancel:hover{
        color: #333!important;
    }
    .note .post .comment-list .new-comment .btn-send{
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
    .note .post .comment-list .new-comment .btn-send:hover{
        background-color: #3db922;
    }
    .note .post .comment-list .new-comment .emoji-modal-wrap .emoji-modal{
        position: absolute;
        top: 50px;
        left: -48px;
        width: 360px;
        height: 100px;
        border: 1px solid #d9d9d9;
        border-radius: 4px;
    }
    .note .post .comment-list .new-comment .emoji-modal-wrap .arrow-up:after{
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
</style>
<script>
    export default {
        name:'myComment',
        data(){
            return{
                send_one:false,
                send_two:false,
                showEmoji:false
            }
        }
    }
</script>