<template>
  <div class="cartcontrol">
    <div
      class="cart-decrease icon-remove_circle_outline"
      v-show="food.count > 0"
      @click.stop.prevent="decreaseCart"
      transition="move"
    >
      <div class="icon-inner-background">-</div>
    </div>
    <div class="cart-count" v-show="food.count > 0">{{food.count}}</div>
    <div class="cart-increase icon-add_circle_outline" @click.stop.prevent="addCart">+</div>
  </div>
</template>

<script type="text/ecmascript-6">
 import Vue from 'vue';
 export default {
    props: {
      food: {
        type: Object
      }
    },
    created() {

    },
    methods: {
      addCart(event) {
        if (!event._constructed) {
          return; // 不是自己派生的return
        }
        if (!this.food.count) {
          Vue.set(this.food, 'count', 1);
        } else {
          this.food.count++;
        }
        this.$dispatch('cart.add', event.target); // 分发cart.add方法
      },
      decreaseCart(event) {
        if (!event._constructed) {
          return; // 不是自己派生的return
        }
        if (this.food.count) {
          this.food.count--;
        }
      }
    }
 };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .cartcontrol
    font-size: 0
    .cart-decrease, .cart-increase
      display: inline-block
      width: 18px
      height: 18px
      line-height: 18px
      font-size: 24px
      text-align: center
      border-radius: 50%
      background: rgb(0, 160, 220)
      vertical-align: bottom
    .cart-decrease
      transition: all .4s linear
      &.move-transition
        opacity: 1
        transform: translate3d(0, 0, 0)
      &.move-enter, &.move-leave
        opacity: 0
        transform: translate3d(24px, 0, 0)
    .cart-count
      display: inline-block
      width: 12px
      padding: 6px 6px 0px 6px
      line-height: 24px
      text-align: center
      font-size: 10px
      color: rgb(147, 153, 159)
      vertical-align: bottom
    .icon-add_circle_outline
      color: #fff
      padding: 3px
    .icon-remove_circle_outline
      color: rgb(0, 160, 220)
      width: 24px
      height: 24px
      position: relative
      .icon-inner-background
        width: 20px
        height: 20px
        background: #fff
        border-radius: 50%
        margin-top: -10px;
        margin-left: -10px;
        left: 50%;
        top: 50%;
        line-height: 20px;
        position: absolute
</style>
