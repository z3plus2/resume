<template>
    <div class="page">
        <v-boxhead name='联系方式'></v-boxhead>
        <ul class="main">
            <li v-for="item in contactMain">
                <a :href="item.contactTo" :class="item.way" class="contact-number">{{item.number}}</a>
            </li>
        </ul>
    </div>
</template>

<script type="text/ecmascript-6">
import boxhead from '../boxhead/boxhead.vue';
export default {
    props: {
        contact: {
            type: Array,
            default: function() {
                return [];
            }
        }
    },
    computed: {
        //利用计算属性，判断是电话还是邮件来给定href的值，根据实际情况这个函数可能应该用通过内容判定 
        contactMain: function() {
            let con = [];
            con = this.contact.map(function(value) {
                let contactTo = value.number;
                if (value.way === "phone") {
                    contactTo = "tel:" + value.number;
                };
                if (value.way === "email") {
                    contactTo = "mailto:" + value.number;
                };
                value.contactTo = contactTo;
                return value;
            });
            return con;
        }
    },
    components: {
        'v-boxhead': boxhead
    }
}
</script>

<style scoped lang="stylus">
.page
  .main
    line-height 1.5em
    .contact-number
      display block
      padding 5px 30px
      overflow visible
      background-repeat no-repeat
      background-size 1.5em
      background-position-y  5px
    .phone
      background-image url(phone.png)
      background-position-x 1px
    .email
      background-image url(email.png)
      background-size 1.8em
      background-position-y  3px
    .homepage
      background-image url(homepage.png)
      background-size 1.6em
      background-position-x 2px
    .github
      background-image url(github.png)
      background-size 1.8em
      background-position-y  3px
</style>
