<template>
  <div class="podcast-item">
    <div>
      <div class="podcast-item__num">
        <p>{{index}}</p>
      </div>
      <div class="podcast-item__des">
        <p class="podcast-item__des__title">{{item.title}}</p>
        <p class="podcast-item__des__detail">{{item.description}}</p>
      </div>
    </div>
    <div class="podcast-item__tag-time">
      <div class="podcast-item__tag-time__tag-wrap">
        <p class="tag-wrap__tag" v-for="tag in item.tag">{{tag}}</p>
      </div>
      <p class="podcast-item__time">{{item.pubDate}}</p>
    </div>
    <span></span>
  </div>
</template>

<script>
export default {
  name: "podcastItem",
  props: ["index", "item", "time", "tag"]
};
</script>

<style lang="scss" scoped>
@import "../style/global.scss";

.podcast-item {
  position: relative;
  width: auto;
  padding: 24px 24px;
  display: flex;
  flex-direction: column;

  & > div {
    display: flex;
    justify-content: space-between;
  }

  &__tag-time {
    display: flex;
    flex-direction: column;
    text-align: right;
    margin-top: 14px;
    @include fontRegular(12px, $gray-2, 12px, 1px);

    &__tag-wrap {
      display: flex;
      justify-content: flex-end;
      margin-bottom: 8px;

      .tag-wrap__tag {
        margin-right: 8px;
        @include fontRegular(12px, $black-3, 12px, 1px);

        &:last-child {
          margin: 0;
        }
      }
    }
  }

  &__num {
    position: relative;
    display: flex;
    justify-content: center;
    width: 50px;
    height: 50px;
    border-radius: 50px;
    cursor: pointer;
    background-color: $black-1;
    margin-top: -8px;
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
    position: relative;
    max-width: 560px;
    padding-bottom: 20px;
    border-bottom: 1px dashed $gray-3;

    &__title {
      display: inline-block;
      margin-bottom: 16px;
      background-color: $black-1;
      padding: 0 6px;
      @include fontBold(20px, $gray-1, 32px, 1px);
    }

    &__detail {
      @include fontRegular(14px, $black-3, 21px, 1px);
    }
    /* &__time {
      position: relative;
      right: 0;
      text-align: right;
      margin-top: 12px;
      @include fontRegular(12px, $gray-2, 12px, 1px);
    } */
  }

  &:hover span {
    opacity: 1;
    transform: scale(1);
  }

  &:hover .podcast-item__des__title {
    background-color: rgba(255, 199, 0, 0.25);
    color: #544100;
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
    top: -6px;
    width: 100%;
    height: 100%;
    background-color: white;
    transition: all 0.7s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    transform: scale(0.98);
    border: 3px solid $black-3;
  }
}
</style>
