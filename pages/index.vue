<template>
    <div>
        <my-header></my-header>
        <div class="index my-container">
            <div class="row">
                <div class="col-8 main">
                    <div class="banner">
                        <nuxt-link to="/">
                            <img src="../assets/img/lunbo1.jpg" >
                        </nuxt-link>
                    </div>
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
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import myHeader from '~/components/myHeader'
    export default {
        components:{
            myHeader
        }
    }
</script>
<style>

</style>