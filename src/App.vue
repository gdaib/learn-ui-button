<template>
  <div class="root-name">
    <div class="button-container">
      <UIButton
        @click="handleClick"
        :large="isSizeType('large')"
        :xlarge="isSizeType('xlarge')"
        :normal="isSizeType('normal')"
        :small="isSizeType('small')"
        :title="isCircleType('title')"
        :rounded="isCircleType('rounded')"
        :circle="isCircleType('circle')"
        :disabled="disabled"
        color="blue"
      >
        Buttond
      </UIButton>
    </div>
    <div class="btn-group">
      <div class="title">size change</div>
      <UIButton @click="resize('xsmall')" xsmall>超小</UIButton>
      <UIButton @click="resize('small')" small>小</UIButton>
      <UIButton @click="resize('normal')">正常</UIButton>
      <UIButton @click="resize('large')" large>大</UIButton>
      <UIButton @click="resize('xlarge')" xlarge>超大</UIButton>
    </div>

    <div class="btn-group">
      <div class="title">circle</div>
      <UIButton @click="reCircleType('title')" title>Title</UIButton>
      <UIButton @click="reCircleType('rounded')" rounded>rounded</UIButton>
      <UIButton @click="reCircleType('circle')" circle>circle</UIButton>
    </div>
    <div class="btn-group">
      <div class="title">state</div>
      <UIButton @click="disabled = !disabled">禁用</UIButton>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import UIButton from "@/components/UIkit/ui-button.vue";

@Component({
  components: {
    UIButton
  }
})
export default class App extends Vue {
  private size = "normal";
  private circleType = "title";
  private disabled = false;

  private isSizeType(size: string) {
    return this.size === size;
  }
  private isCircleType(type: string) {
    return this.circleType === type;
  }

  private handleClick(e: MouseEvent) {
    console.log("hello world", typeof e, e);
  }

  private resize(size: string) {
    this.size = size;
  }
  private reCircleType(type: string) {
    this.circleType = type;
  }
}
</script>

<style lang="less">
.root-name {
  .button-container {
    width: 480px;
    height: 160px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
  }
  .btn-group {
    margin-bottom: 10px;
    > button {
      margin: 0 6px;
    }
  }
}
</style>
