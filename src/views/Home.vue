<template>
  <div class="home">
    <div class="player">
      <div class="cover"></div>
      <audio :src="link" controls></audio>
    </div>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      link:
        "http://pojj9t7wl.bkt.clouddn.com/%E6%99%AE%E9%80%9A%E5%9C%86-%E7%AC%AC1%E6%9C%9F%20-%202019:3:17%20%E4%B8%8B%E5%8D%885.49.mp3"
    };
  }
};
</script>

<style lang="scss" scoped>
.home {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;

  .player {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    .cover {
      width: 240px;
      height: 240px;
      border-radius: 8px;
      background: url('../assets/cover.jpg') no-repeat;
      background-size: cover;
      margin-bottom: 24px;
    }
  }
}
</style>

