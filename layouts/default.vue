<template>
  <div id="default-template">
    <nuxt/>
  </div>
</template>
<script>
import Vue from 'vue'
import BootstrapVue from 'bootstrap-vue'
Vue.use(BootstrapVue)
//时间过滤器
Vue.filter('formatDate',function (value) {
    let date = new Date(value)
    let year = date.getFullYear()
    let month = date.getMonth()+1
    let day = date.getDate()
    let hour = date.getHours()
    let minute = date.getMinutes()
    function filter(num) {
        return num > 10 ? num : '0' + num
    }
    return filter(year)+'.'+filter(month)+'.'+filter(day)+' '+filter(hour)+':'+filter(minute);
})
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
export default {

}
</script>
