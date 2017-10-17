<template>
    <div class="page">
        <v-boxhead name="我的作品"></v-boxhead>
        <div class="worksbox">
            <div v-for="item in works" class="works" @click="showMore(item)">
                <h2 class="work-name">{{item.name}}</h2>
                <p>{{item.detail}}</p>
            </div>
            <transition name="fade"><div v-show="moreShow" class="more">

                <div class="more-detail">
                    <img :src="'/static/image/work'+selectWork.image+'.png'" class="more-image">
                    <h2 class="work-name">{{selectWork.name}}</h2>
                    <h3>{{selectWork.more}}</h3>
                    <a href="selectWork.url">{{selectWork.url}}</a>
                    <a href="selectWork.github">{{selectWork.github}}</a>
                </div>
                <p class="closemore" @click="closeMore">ⓧ</p>
            </div></transition>
        </div>

    </div>
</template>

<script type="text/ecmascript-6">
import boxhead from '../boxhead/boxhead.vue';
export default {
    props: {
        works: {
            type: Array,
            default: function() {
                return [];
            }
        }
    },
    data() {
        return {
            selectWork: { image: "loading" },
            moreShow: false
        };
    },
    methods: {
        showMore(work) {
            this.selectWork = work;
            this.moreShow = true;
        },
        closeMore() {
            this.moreShow = false;
        }
    },
    components: {
        'v-boxhead': boxhead
    }
}
</script>

<style scoped lang="stylus">
.page {
    margin-bottom: 50px;

    .worksbox {
        text-align: center;

        .works {
            display: inline-block;
            width: 240px;
            border: 1px solid #e0e0e0;
            margin: 10px 30px 10px 0px;
            padding: 20px;
            text-align: left;
            box-shadow: 1px 1px 8px #ddd;
            cursor: pointer;
            &:active { 
              box-shadow: inset 1px 1px 8px #ddd;
              background-color #efefef;
            }
            p {
                color: #777;
                font-weight: 400;
                margin: 5px 0px;
            }
        }

        .work-name {
            color: green;
            margin-bottom: 10px;
            font-weight: bold;
        }

        .more {
            position: fixed;
            z-index: 50;
            width: 50%;
            min-width: 260px;
            max-width: 600px;
            height: auto;
            left: 0;
            right: 0;
            margin: 0 auto;
            top: 30%;
            border-radius: 15px;
            padding: 20px;
            text-align: left;
            border: 2px solid #d0d0d0;
            background-color: rgba(255, 239, 213, 0.9);
            background-filter: blur(10px);
        &.fade-enter-active{
              transition: all 0.5s 
            }
        &.fade-enter, &.fade-leave{
                opacity 0
                background-color: rgba(255, 239, 213, 0);
                width 0
                height 0
            }

            .more-detail {
                color: #333;
                line-height: 1.2em;
            }
                .work-name {
                }
                h3{
                  font-size 0.8em
                  letter-spacing 3px
                  margin-bottom 30px
                }
                .more-image {
                    max-height: 220px;
                    max-width: 45%;
                    float: right;
                    margin 10px;
                }
                a {
                    display block
                    word-wrap:break-word
                    margin 20px 0
                }

            .closemore {
                position: absolute;
                right: -27px;
                top: -27px;
                font-size: 35px;
                margin: 15px;
                cursor: pointer;
                color: #777;
            }
        }
    }
}
</style>



