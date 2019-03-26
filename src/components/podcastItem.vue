<template>
  <div class="podcast-item">
    <div>
      <div
        :class="{'playBtn1':isBtn}"
        class="podcast-item__num"
        v-for="audioLink in item.enclosure[0]"
        v-on:click="switchPlay(audioLink)"
      >
        <p>{{index}}</p>
      </div>
      <div class="podcast-item__des">
        <p class="podcast-item__des__title">{{item.title}}</p>
        <p class="podcast-item__des__detail">{{item.description}}</p>
      </div>
    </div>
    <div class="podcast-item__tag-time">
      <div class="podcast-item__tag-time__duration">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
          <path
            d="M11.99 2C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zM12 20c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8z"
          ></path>
          <path d="M0 0h24v24H0z" fill="none"></path>
          <path d="M12.5 7H11v6l5.25 3.15.75-1.23-4.5-2.67z"></path>
        </svg>
        <p>{{item.duration}}</p>
      </div>
      <div class="podcast-item__tag-time__tag-wrap">
        <p class="tag-wrap__tag" v-for="tag in item.tag">{{tag}}</p>
      </div>
      <p class="podcast-item__time">{{item.pubDate}}</p>
    </div>
    <span></span>
  </div>
</template>

<script>
import dataJson from "../data.json";

export default {
  name: "podcastItem",
  props: ["index", "item", "time", "tag", "audioLink"],
  data() {
    return {
      isNum: true,
      // isBtn: isBtn2(),
      isBtn:  function() {
        let audio = document.getElementById("audio");
        if (audio.play) {
          return false;
        } else {
          return false;
        }
      }
    };
  },
  mounted() {
    // let playBtn = document.getElementsByClassName("playBtn");
    // let audioLink = document.getElementsByClassName("audioLink");
  },
  methods: {
    switchPlay: function(e) {
      audio.setAttribute("src", e);
      function audioPlay() {
        // let playBtn = document.getElementsByClassName("playBtn");
        if (audio.paused) {
          audio.play();
          play.style.display = "none";
          pause.style.display = "block";
        }
      }

      function audioPause() {
        audio.pause();
        pause.style.display = "none";
        play.style.display = "block";
      }
      audioPlay();
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../style/global.scss";

.playBtn1 {
  p {
    display: none;
  }
  &::before {
    opacity: 1 !important;
  }
}

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
    position: relative;
    display: flex;
    flex-direction: column;
    text-align: right;
    margin-top: 14px;
    @include fontRegular(12px, $gray-2, 12px, 1px);

    &__duration {
      position: absolute;
      top: -6px;
      height: 20px;
      text-align: left;
      padding-left: 80px;

      svg {
        width: 18px;
        position: absolute;
        top: 0;
        fill: $gray-2;
      }

      p {
        padding-left: 24px;
        @include fontRegular(12px, $gray-2, 23px, 1px);
      }
    }
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

    &:after {
      content: "";
      position: absolute;
      top: 9px;
      display: block;
      width: 32px;
      height: 32px;
      background: url("../assets/pause.svg") no-repeat;
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
    top: -4px;
    width: 100%;
    height: 100%;
    background-color: white;
    transition: all 0.7s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    transform: scale(0.98);
    /* border: 3px solid $black-3; */
    box-shadow: 0 32px 40px rgba(51, 51, 51, 0.08);
  }
}
</style>
