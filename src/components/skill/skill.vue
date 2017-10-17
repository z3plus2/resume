<template>
    <div class="page">
        <v-boxhead name="技术能力"></v-boxhead>
        <div class="skillbox">
            <div v-for="item in skill" class="skill" :class="'skill'+item[1]">{{item[0]}}</div>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
import boxhead from '../boxhead/boxhead.vue';
export default {
    props: {
        skill: {
            type: Array,
            default: function() {
                return [['skill', '0']];
            }
        }
    },
    components: {
        'v-boxhead': boxhead
    }
}
</script>

<style scoped lang="stylus">
.page 
    margin: 10px 0px;
    text-align: left;
    .skillbox
        margin-bottom: 50px;
        .skill 
            border-radius: 0.4rem;
            background-color: rgba(210, 110, 10, 0.3);
            display: inline-block;
            font-size: 16px;
            margin: 12px 5px;
            letter-spacing: 0.1rem;
            line-height: 1.5rem;
            padding: 4px 1rem;
            text-align: center;
            text-decoration: none;
            white-space: nowrap;
        .skill1 
            background-color: rgba(200, 200, 200, 0.3);
       


</style>
