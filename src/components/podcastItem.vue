<template>
  <div class="podcast-item">
    <div class="podcast-item__num">
      <p>{{index}}</p>
    </div>
    <div class="podcast-item__des">
      <p class="podcast-item__des__title">{{item.title}}</p>
      <p class="podcast-item__des__detail">{{item.description}}</p>
    </div>
    <span></span>
  </div>
</template>

<script>
export default {
  name: "podcastItem",
  props: ['index', 'item'],
};
</script>

<style lang="scss" scoped>
@import "../style/global.scss";

.podcast-item {
  position: relative;
  width: auto;
  padding: 40px 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  &__num {
    position: relative;
    display: flex;
    justify-content: center;
    width: 50px;
    height: 50px;
    border-radius: 50px;
    cursor: pointer;
    background-color: $black-1;
    transition-delay: 0.3s;
    transition: all 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    @include fontCrimson(34px, $gray-1, 58px, 0);

    &:before {
      content: "";
      position: absolute;
      top: 9px;
      display: block;
      width: 32px;
      height: 32px;
      background: url("../assets/listPlay.svg") no-repeat;
      background-size: cover;
      opacity: 0;
      transition-delay: 0.2s;
      transform: scale(0.85);
      transition: all 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }

    p {
      transition: all 0.2s ease;
    }
  }

  &__des {
    max-width: 560px;

    &__title {
      margin-bottom: 8px;
      @include fontBold(24px, $black-1, 58px, 1px);
    }

    &__detail {
      @include fontRegular(14px, $black-3, 21px, 1px);
    }
  }

  &:hover span {
    opacity: 1;
    transform: scale(1);
  }

  &:hover .podcast-item__num {
    transform: scale(1.1);
    p {
      transform: scale(0.6);
      opacity: 0;
    }
    &::before {
      opacity: 1;
      transform: scale(1);
    }
  }

  span {
    opacity: 0;
    z-index: -1;
    display: inline-block;
    position: absolute;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: $gray-3;
    transition: all 0.7s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    transform: scale(0.98);
  }
}
</style>
