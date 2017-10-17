<template>
    <div class="page">
        <v-boxhead name='自我介绍'></v-boxhead>
        <p v-for="item in introd.main" class="info">{{item}}</p>
        <div class="more-info" @click="show">
            <div class="more-switch" :class="{open:moreShow}">{{toggle}}</div>
            <div v-show="moreShow" class="more-main">
                <ul>
                    <li v-for="item in introd.more" class="more-list">{{item.mode}}: {{item.value}}</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
import boxhead from '../boxhead/boxhead.vue';
export default {
    props: {
        introd: {
            type: Object,
            default: function() {
                return {
                    main: []
                }
            }
        }
    },
    data() {
        return {
            moreShow: false,
            toggle: "更多"
        };
    },
    methods: {
        show: function() {
            this.moreShow = !this.moreShow;
            if (this.toggle === "更多") {
                this.toggle = "关闭";
                return;
            };
            this.toggle = "更多"
        }
    },
    components: {
        'v-boxhead': boxhead
    }
}
</script>

<style scoped lang="stylus">
.page
  position relative
  .info
    display block
    margin 10px 0px
    line-height 1.5rem
    &:last-child
      margin-bottom 50px
  .more-info
     position absolute
     right 5px
     top 5px
     color #555
     .more-switch
       position absolute
       display block
       right 0 
       top 0
       width 38px 
       text-align center
       padding 3px
       cursor pointer
       border-radius 5px 5px 5px 5px
       background-color rgba(255, 165, 85, 0.9)
       box-shadow 1px 1px 2px #866
       &:active
         box-shadow inset 1px 1px 2px #ddd

      .open    
       border-radius 5px 5px 0px 0px
       box-shadow: 0 0 0
      .more-main
        position absolute
        right 0
        top 20px
        padding 5px
        border-radius 5px 0px 5px 5px
        background-color rgba(255, 165, 85, 1)
      .more-list
        line-height 25px
        white-space: nowrap
        
</style>
