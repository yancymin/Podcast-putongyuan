<template>
  <div class="home">
    <audio :src='link' controls></audio>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      link:
        "http://yancymin.oss-cn-beijing.aliyuncs.com/%E6%99%AE%E9%80%9A%E5%9C%86-%E7%AC%AC1%E6%9C%9F%20-%202019%3A3%3A17%20%E4%B8%8B%E5%8D%885.49-1.mp3?Expires=1552835645&OSSAccessKeyId=TMP.AQEY_ynRU5jCsJVDCM-RLvctFdc3S5shPVjdmvv_5SKql0omeflSqDTorp9HADAtAhRiq-vm_HT-fnraUR5lDwj8Q-ul4wIVAJNA_KNYE7P0MmBfHuhyNKqaUsSA&Signature=2wOX4wHEYcqZC5kZ%2FLgX9J6bMbs%3D"
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
}
</style>

