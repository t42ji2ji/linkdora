<template lang="pug">
  a.Link(:href="Linkurl" target="_blank") {{LinkTitle}}
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
  }
};
</script>

<style lang="sass">


.Link
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
  



@media screen and (max-device-width: 480px)
  .Link
    max-width: 60%

</style>