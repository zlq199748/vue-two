<template>
  <div class="star" :class="'star-'+size">                           <!--动态添加类名-->
    <span class="star-item" v-for="(c,index) in starClasser" :key="index" :class="c"></span>
  </div>
</template>
<script>
  export default{
    computed:{
      starClasser(){
         const {score}=this //评分
        const  arr=[]
        const scoreInteger =Math.floor(score)
        for (let i = 0; i < scoreInteger; i++) {
         arr.push('on')
        }
        if (score-scoreInteger>=0.5){
           arr.push('half')
        }
        if(arr.length<5){
          arr.push('off')
        }
       return arr
      }

    },
    props:{
      score:Number,
      size:Number
    }
  }

</script>
<style lang="stylus" rel="stylesheet/stylus" scoped>
  @import '../../common/stylus/mixins.styl';
  .star //2x图 3x图
    float left
    font-size 0
    .star-item
      display inline-block
      background-repeat no-repeat
    &.star-48
      .star-item
        width 20px
        height 20px
        margin-right 22px
        background-size 20px 20px
        &:last-child
          margin-right: 0
        &.on
          bg-image('./images/star48_on')
        &.half
          bg-image('./images/star48_half')
        &.off
          bg-image('./images/star48_off')
    &.star-36
      .star-item
        width 15px
        height 15px
        margin-right 6px
        background-size 15px 15px
        &:last-child·
          margin-right 0
        &.on
          bg-image('./images/star36_on')
        &.half
          bg-image('./images/star36_half')
        &.off
          bg-image('./images/star36_off')
    &.star-24
      .star-item
        width 10px
        height 10px
        margin-right 3px
        background-size 10px 10px
        &:last-child
          margin-right 0
        &.on
          bg-image('./images/star24_on')
        &.half
          bg-image('./images/star24_half')
        &.off
          bg-image('./images/star24_off')
</style>
