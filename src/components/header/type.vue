<template>
  <span class="icon" :class="[iconSize, classMap[type] + size]">
  </span>
</template>

<script type="text/ecmascript-6">
 export default {
  props: {
    type: {
      type: Number
    },
    size: {
      type: Number
    }
  },
  data() {
    return {
      iconSize: 'size' + this.size
    };
  },
  created() {
    this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
  }
 };
</script>

<style lang="stylus" rel="stylesheet/stylus">
   @import "../../common/stylus/mixin";
  .icon
    display: inline-block
    vertical-align: top
    margin-right: 2px
    background-repeat: no-repeat
    &.size12
      width: 12px
      height: 12px
      background-size: 12px 12px
    &.size24
      width: 24px
      height: 24px
      background-size: 24px 24px
    &.size36
      width: 36px
      height: 36px
      background-size: 36px 36px
    &.decrease12
      bg-image('./decrease_3')
    &.discount12
      bg-image('./discount_3')
    &.special12
      bg-image('./special_3')
    &.invoice12
      bg-image('./invoice_3')
    &.guarantee12
      bg-image('./guarantee_3')
    &.decrease24
      bg-image('./decrease_2')
    &.discount24
      bg-image('./discount_2')
    &.special24
      bg-image('./special_2')
    &.invoice24
      bg-image('./invoice_2')
    &.guarantee24
      bg-image('./guarantee_2')
    &.decrease36
      bg-image('./decrease_3')
    &.discount36
      bg-image('./discount_3')
    &.special36
      bg-image('./special_3')
    &.invoice36
      bg-image('./invoice_3')
    &.guarantee36
      bg-image('./guarantee_3')
</style>
