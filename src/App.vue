<style scoped>
.big_boss {
  position: relative;
  width: 100%;
}
img {
  width: 100%;
}
img.banner {
  border: 20px solid #e8e8e8;
  box-sizing: border-box;
}
.recommend_day {
  margin: 30px auto;
  width: 200px;
  height: 50px;
  background: rgb(203, 233, 225);
  text-align: center;
  line-height: 50px;
  color: rgb(72, 174, 167);
  font-size: 26px;
  border-radius: 25px;
}
.recommend_day_list {
  margin-top: 50px;
  list-style: none;
  width: 100%;
  padding: 0px;
  /* margin:  0 auto; */
}
.recommend_day_list li {
  float: left;
  width: 49%;
  /* margin-left: 25px; */
}
.recommend_day_list li img {
  width: 100%;
  height: 300px;
}
.recommend_day_list li:nth-child(2n) {
  margin-left: 2%;
}
</style>
<template>
    <div class="big_boss">
        <div class="banner">
            <img :src="bannerimg" class="banner">
        </div>
        <div class="recommend_day">每日推荐</div>
        <ul class="recommend_day_list">
          <li  v-for="(item,index) in soundpic" :key="index">
            <img :src="item.sound.pic">
        </li>
        </ul>
    </div>
</template>
<script>
export default {
  data() {
    return {
      bannerimg: "",
      soundpic: []
    }
  },
  mounted() {
    this.axios.get("../static/data1.json").then((data) => {
      this.bannerimg = data.data.banner.sound.pic_big
      // console.log(data.data.banner.sound)
    });
    this.axios.get("../static/data1.json").then((data) => {
      this.soundpic = data.data.recommend_day
      console.log(this.soundpic)
    });
  }
}
</script>