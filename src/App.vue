<template lang="pug">
  #app
    .Links
      .head
        .headimage(@click="add")
        .headTitle
          h1 Hi 我是哆啦
          h4 這是我的小天地
      <hr style="width: 70%; margin-bottom: 30px">
      transition-group(name="list" tag="div" class="df")
        DoraLink(v-for ="(data, index) in links" :LinkTitle="data.title", :Linkurl="data.url" :key="index + 0")
</template>

<script>
import DoraLink from "./components/DoraLink";
import { setTimeout } from "timers";
import { page } from 'vue-analytics';

export default {
  name: "app",
  components: {
    DoraLink
  },
  data() {
    return {
      data: [
        {
          title: "最新文章",
          url:
            "https://medium.com/%E5%93%86%E5%95%A6%E5%AF%A6%E9%A9%97%E5%AE%A4/%E8%87%AA%E6%88%91%E6%98%AF%E5%8D%A1%E5%9C%A8%E6%B4%9E%E5%8F%A3%E7%9A%84-%E4%BA%BA%E7%94%9F%E8%A8%88%E7%95%AB-1-bd0a92190add"
        },
        {
          title: "Facebook",
          url: "https://www.facebook.com/doraralab/"
        },
        {
          title: "",
          url: ""
        },
        {
          title: "我的貼圖",
          url: "https://store.line.me/stickershop/product/7662172/zh-Hant"
        },
      ],
      links: [],
      show: true
    };
  },
  mounted() {
    var vm = this;
    this.data.forEach(function(item, index) {
      (function() {
        setTimeout(function(){
          vm.links.push(item)
        }, index*500)
      }(index))
    });
  },
  methods: {
    add: function() {
      this.links.push({
        title: "Facebook",
        url: ""
      });
      this.$ga.event('HeadImage', 'click', 'headImageClick', 1)
    },
    track() {
      page('/')
    }
  }
};
</script>

<style lang="sass">
  @import url('https://fonts.googleapis.com/css?family=Noto+Sans+TC&display=swap')

  @mixin size($w,$h:$w)
    width: $w
    height: $h
    

  html, body
    width: 100%
    height: 100%
    margin: 0
    background-color: #222938
    font-family: 'Noto Sans TC', sans-
    hr
      opacity: .8
  
  .df
    width: 100%
    display: flex
    align-items: center
    flex-direction: column
    margin-bottom: 10%


  #app
    +size(100%)
    display: flex
    justify-content: center
    h1
      margin: 0
      color: white
    h4
      margin: 0

  .Links
    width: 100%
    display: flex
    align-items: center
    flex-direction: column
    transition: .5s
    margin-top: 20vh
  .head
    padding: 15px 12px
    display: flex
    align-items: center
    .headimage
      +size(80px)
      background-color: #f27474
      margin: 5px
      border-radius: 50%
      background-image: url('./assets/pig.png')
      background-position: center center
      background-repeat: no-repeat
      background-size: cover

    .headTitle
      text-align: left
      color: white
      margin: 5px
      h1
        font-size: 1.5rem
      h4
        color: rgba(white, .3)


.list-item
  display: inline-block
  margin-right: 10px

.list-enter-active, .list-leave-active
  transition: all 1s

.list-enter, .list-leave-to
  opacity: 0
  transform: translateY(30px)
</style>
