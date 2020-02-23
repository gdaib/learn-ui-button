<template>
  <button
    class="ui-button"
    @click="onClickButton"
    :class="{
      'ui-button-large': large,
      'ui-button-xlarge': xlarge,
      'ui-button-small': small,
      'ui-button-xsmall': xsmall,
      'ui-button-title': title,
      'ui-button-rounded': rounded,
      'ui-button-circle': circle,
      'ui-button-disabled': disabled
    }"
    :style="`--color-tint: ${tintColor}`"
  >
    <slot />
  </button>
</template>

<script lang="ts">
import { Component, Vue, Emit, Prop } from "vue-property-decorator";

@Component
export default class UIButton extends Vue {
  @Prop(Boolean) private large: boolean | undefined;
  @Prop(Boolean) private xlarge: boolean | undefined;
  @Prop(Boolean) private small: boolean | undefined;
  @Prop(Boolean) private xsmall: boolean | undefined;

  @Prop(Boolean) private title: boolean | undefined;
  @Prop(Boolean) private rounded: boolean | undefined;
  @Prop(Boolean) private circle: boolean | undefined;

  @Prop(Boolean) private disabled: boolean | undefined;

  @Prop(String) private color: string | undefined;

  private get tintColor() {
    return this.color || "#2d8cf0";
  }

  // eslint-disable-next-line
  @Emit("click") private emitClickEvent(event: MouseEvent) {}

  private mounted() {
    console.log(this.large);
  }

  private onClickButton(event: MouseEvent) {
    if (this.disabled) return;
    this.emitClickEvent(event);
  }
}
</script>

<style lang="less">
.resize (@minWidth, @height, @paddingLR, @fongSize) {
  min-width: @minWidth;
  height: @height;
  padding: 0 @paddingLR;
  font-size: @fongSize;

  &.ui-button {
    &-rounded,
    &-circle {
      border-radius: (@height / 2);
    }
    &-circle {
      width: @height;
      min-width: 0;
      padding: 0;
    }
  }
}

.ui-button {
  .resize(64px, 36px, 16px, 0.875rem);
  border: 0 solid black;
  outline: none;
  font-weight: 500;
  letter-spacing: 0.09em;
  color: #17233d;
  background: var(--color-tint);
  cursor: pointer;
  user-select: none;

  &:hover {
    filter: brightness(120%);
  }
  &:active {
    filter: brightness(80%);
  }

  &-xsmall {
    .resize(36px, 20px, 9px, 0.625rem);
  }
  &-small {
    .resize(50px, 28px, 12px, 0.75rem);
  }
  &-large {
    .resize(78px, 44px, 19px, 0.875rem);
  }
  &-xlarge {
    .resize(92px, 52px, 23px, 1rem);
  }

  &-title {
    border-radius: 0;
  }

  &-disabled {
    background: #f5f5f5;
    cursor: not-allowed;
    color: #c5c8ce;
  }
}
</style>
