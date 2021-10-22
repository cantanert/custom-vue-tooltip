<template>
    <div
      :class="`dark-tooltip-wrapper ${placementClasses}`"
      :style="{
        top: top,
        bottom: bottom,
        left: left,
        right: right,
        ...tooltipStyles,
      }"
    >
      <slot name="tooltipContent"/>
    </div>
</template>

<script>
  export default {
    name: "DarkTooltip",
    props: {
      tooltipStyles: {
        type: Object,
        default: {}
      },
      top: {
        type: String,
        default: "unset"
      },
      bottom: {
        type: String,
        default: "unset"
      },
      left: {
        type: String,
        default: "unset"
      },
      right: {
        type: String,
        default: "unset"
      },
      placement: {
        type: String,
        default: "bottom"
      },
      /*top, top-left, top-right, bottom, bottom-left, bottom-right, left, right*/
    },
    data(){
      return {

      }
    },
    computed: {
      placementClasses(){
        return this.placement.includes('-')
          ? `${this.placement.split("-")[0]} ${this.placement}`
          : this.placement
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import '@/assets/styles/variables.scss';
  .dark-tooltip-wrapper{
    background-color: $dark-gray-4;
    color: $white-1;
    border-radius: 6px;
    font-size: 12px;
    font-weight: 600;
    padding: 12px;
    position: absolute;
    right: calc(50% - 5px);
    width: auto;
    p{
      white-space: nowrap;
    }
    &.bottom{
      :before{
        content: '';
        color: $dark-gray-4;
        border-top: 5px solid transparent;
        border-left: 5px solid transparent;
        border-right: 5px solid transparent;
        border-bottom: 5px solid;
        position: absolute;
        top:-10px;
        right: calc(50% - 5px)
      }
      &-left{
        :before{
          left: unset;
          right: 20px;
        }
      }
      &-right{
        :before{
          left: 20px;
          right: unset;
        }
      }
    }
    &.top{
      :before{
        content: '';
        color: $dark-gray-4;
        border-bottom: 5px solid transparent;
        border-left: 5px solid transparent;
        border-right: 5px solid transparent;
        border-top: 5px solid;
        position: absolute;
        bottom: -10px;
        right: calc(50% - 5px)
      }
      &-left{
        :before{
          left: unset;
          right: 20px;
        }
      }
      &-right{
        :before{
          left: 20px;
          right: unset;
        }
      }
    }
    &.left{
      :before{
        content: '';
        color: $dark-gray-4;
        border-bottom: 5px solid transparent;
        border-right: 5px solid transparent;
        border-top: 5px solid transparent;
        border-left: 5px solid;
        position: absolute;
        bottom: calc(50% - 5px);
        right: -10px
      }
    }
    &.right{
      :before{
        content: '';
        color: $dark-gray-4;
        border-bottom: 5px solid transparent;
        border-left: 5px solid transparent;
        border-top: 5px solid transparent;
        border-right: 5px solid;
        position: absolute;
        bottom: calc(50% - 5px);
        left: -10px
      }
    }
  }
</style>
