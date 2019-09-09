<template lang="pug">
  a.Link(:href="Linkurl" target="_blank" @click="click(LinkTitle)" :style="show") {{LinkTitle}}
</template>

<script>
export default {
  name: "app",
  components: {},
  props: {
    Linkurl: String, LinkTitle:String,
  },
  data: function() {
    return {
      title: "asd",
    };
  },
  computed:{
    show: function() {
      if(this.LinkTitle == ""){
        return {
          opacity: '0',
          margin: '0',
          'pointer-events': 'none'
        }
      }
      return ""
    }
  },
  methods: {
    click: function(title) {
      console.log(title);
      this.$ga.event('Link', 'click', title, 1)
    }
  }
};
</script>

<style lang="sass">


.Link
  min-height: 1.3rem
  max-width: 60%
  padding: 7px 22px
  background-color: white
  text-align: center
  width: 100%
  border-radius: 7px
  font-size: 1.3rem
  font-weight: bold
  cursor: pointer
  text-decoration: none
  color: #573b95
  margin-bottom: 15px
  flex: 1
  cursor: pointer
  



@media screen and (max-device-width: 480px)
  .Link
    max-width: 60%

</style>