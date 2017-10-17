<template>
    <div class="page">
        <v-boxhead name='个人经历'></v-boxhead>
        <ul class="main">
            <li v-for="item in experience">
                <h2 class="unit">{{item.unit}}</h2>
                <p class="post">{{item.post}}</p>
                <p class="time">{{item.time}}</p>
            </li>
        </ul>
    </div>
</template>

<script type="text/ecmascript-6">
import boxhead from '../boxhead/boxhead.vue';
export default {
    props: {
        experience: {
            type: Array,
            default: function() {
                return [];
            }
        }
    },
    components: {
        'v-boxhead': boxhead
    }
}
</script>

<style scoped lang="stylus">
.main
  line-height 1.5em
  margin-bottom 30px
  .unit
    font-weight bold
  .post
    display inline-block 
    color #666
    width 60%
  .time
    display inline-block
    width 100px
    float right 
    color #666
</style>
