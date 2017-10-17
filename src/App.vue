<template>
  <div id="app">
    <v-header :resumea="resume.resumea"></v-header>
    <v-introduction v-bind:introd="resume.introduction"></v-introduction>
    <v-works :works="resume.works"></v-works>
    <v-skill :skill="resume.skill"></v-skill>
    <v-experience :experience="resume.experience"></v-experience>
    <v-contact :contact="resume.contact"></v-contact>
  </div>
</template>

<script type="text/ecmascript-6">
import header from './components/header/header.vue';
import introduction from './components/introduction/introduction.vue';
import skill from './components/skill/skill.vue';
import works from './components/works/works.vue';
import experience from './components/experience/experience.vue';
import contact from './components/contact/contact.vue';

const ERR_OK = 0;

export default {
  name: 'app',
  data() {
    return {
      resume: {}
    };
  },
  created() {
    this.$http.get('/api/resume').then((response) => {
      response = response.body;
      if (response.errno === ERR_OK) {
        this.resume=response.data;
        };
        console.log(this.resume)

    })
  },
  components: {
    'v-header': header,
    'v-introduction': introduction,
    'v-skill': skill,
    'v-works': works,
    'v-experience':experience,
    'v-contact':contact
  }
}
</script>

<style scoped lang="stylus">
   #app
    max-width: 640px;
    margin: 0 auto;
    margin-top: auto;
    margin-bottom: auto;
    padding: 3rem;
    background-color: #ffe;
    box-shadow: 1px 1px 6px #ddd;
    border-radius: 2px;
</style>
