<template>
  <div>
    <loading v-if="!isReady"></loading>
    <div v-if="isReady">
      <page-title :showBack="true">{{movieDetail.nm}}</page-title>
      <div class="movie-header">
         <!-- 设置背景模糊 -->
        <div class="bg-last">
          <img :src="movieDetail.img.replace('w.h','128.180')">
        </div>
        <div class="bg-fliter"></div>
        <!-- 左侧海报 -->
        <div class="movie-img">
          <img @click="showPlayVD=true" :src="movieDetail.img.replace('w.h','128.180')" alt>
        </div>
        <!-- 右侧信息 -->
        <ul class="movie-info">
          <li class="name">{{movieDetail.nm}}</li>
          <!-- <li class="enm">{{movieDetail.enm}}</li> -->
          <li v-if="movieDetail.globalReleased && movieDetail.sc!==0" class="score">
            观众评
            <span>{{movieDetail.sc}}</span>
          </li>
          <li
            style="font-size: 14px;color: #888"
            v-if="movieDetail.globalReleased && movieDetail.sc==0"
          >暂无评分</li>
          <li v-if="!movieDetail.globalReleased" class="score">
            <span>{{movieDetail.wish}}</span> 想看
          </li>
          <li>{{movieDetail.type}}</li>
          <li>{{movieDetail.place}}</li>
          <li>{{movieDetail.rt}} 上映</li>
        </ul>
      </div>

      <button class="buy-btn">特惠购票</button>
      
      <!-- 查看全部介绍开关 -->
      <div class="movie-intro">
        <p :class="btnType?'overflowClose':'overflowOpen'">{{movieDetail.introduce}}</p>
        <img @click="btnType=!btnType" class="btn" :src="btnType?downBtnSrc:upBtnSrc" alt>
      </div>

      

      <!-- 播放电影宣传片  -->
      <div class="play-vd" v-if="showPlayVD" @click="showPlayVD=false">
        <video controls autoplay :src="movieDetail.vd" width="100%"></video>
        <!-- video标签：       autoplay:视频在就绪后马上播放。   controls:向用户显示控件，比如播放按钮
        loop:当媒介文件完成播放后再次开始播放   poster='url':视频下载时显示的图像，或者在用户点击播放按钮前显示的图像 -->
      </div>
    </div>
  </div>
</template>

<script>
// import axios from "axios";
/**
 * img里面的src非常特殊 不能使用表达式动态绑定
 * 如果非要使用动态表达式绑定，一定是先把图片导入进来，然后再使用
 */
import downBtnSrc from "../assets/img/down.png";
import upBtnSrc from "../assets/img/up.png";
import movieDetails from "../../static/movieSources/movieDetails";
// import  movieDetails from "../../movieSources/movieDetails"; 

export default {
  data() {
    return {
      movieDetails: null,
      movieDetail: null,
      btnType: true,
      downBtnSrc,
      upBtnSrc,
      showPlayVD:false,
      isReady:0
    };
  },
  // 这里会在实例创建完成后被立即调用。created 是vue生命周期钩子，参考 https://cn.vuejs.org/v2/api/#created
  created() {
    this.movieDetails=movieDetails.movieDetails.details
    console.log(movieDetails.movieDetails.details)
    this.isReady=1
    // 这里获取 从路由传值传过来的电影id，然后进行数据请求
    let id = this.$route.query.id;
    let userinfoIndex = this.movieDetails.findIndex(info => info.id === id)
    this.movieDetail=this.movieDetails[userinfoIndex]
    console.log(this.movieDetail)
    // this.$axios
    //   .get("http://www.softeem.xin/maoyanApi/ajax/detailmovie?movieId=" + id)
    //   .then(res => {
    //     this.movieDetail = res.data.detailMovie;
    //   });
  },
  methods:{
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/main.scss";
@import "../assets/css/movie-list.css";

.movie-header {
  @include flex-box(row, left, center);

  height: 165px;
  width: 100%;

  >.bg-last {
    position: absolute;
    width: 100%;
    height: 165px;
    z-index: -2;
    overflow: hidden;

    >img {
      width: 100%;
      height: 100%;
      -webkit-filter: blur(27px); /* Chrome, Safari, Opera */
      filter: blur(27px);   /*filter 属性定义了元素(通常是<img>)的模糊与饱和度 blur()是高斯模糊*/
    }
  }

  >.bg-fliter {
    height: 165px;
    width: 100%;
    background-color: #40454d;
    opacity: 0.55;
    position: absolute;
    z-index: -1;
  }

  >.movie-info {
    height: 135px;
    font-size: 12.5px;
    color: #e6e0e0;

    >.name {
      font-size: 16px;
      color: #fbfbfb;
      font-weight: normal;
      margin-bottom: 6px;
    }

  }

  >.movie-img {
    margin-left: 15px;
    position: relative;

    img {
      width: 96.5px;
      height: 135px;
    }

    &:after {    /* 在嵌套的代码块内，可以使用&引用父元素。比如a:hover伪类，可以写成 */
      content: "▶";
      color: #fff;
      font-size: 14px;
      width: 22px;
      height: 22px;
      border-radius: 50%;
      border: 1px solid #fff;
      position: absolute;
      right: 12px;
      bottom: 8px;
      line-height: 22px;
      text-align: center;
      background-color: #333;
      opacity: 0.8;
    }
  }
}

.buy-btn {
  width: calc(100% - 30px);
  margin: 13px 15px;
  padding: 9px;
  font-size: 16px;
  color: #fff;
  text-align: center;
  border-radius: 4px;
  border: none;
  background-color: #e54847;
  position:fixed;
  bottom:5px;

  
}



.movie-intro {
  // text-align: center;
  width: 100%;
  padding: 10px 16px;
  position:relative;

  >p {
    font-size: 14px;
    color: #666;
    overflow: hidden;
    text-overflow: ellipsis;
    padding-top:5px;
  }

  >.btn {
    width: 16px;
    height: 16px;
    display: block;
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
  }
  .overflowClose {
    max-height: 60px;
  }

  .overflowOpen{
    max-height: 160px;
    display: -webkit-box;
    overflow-y: auto;

      /*适应苹果*/
    -webkit-overflow-scrolling: touch;
  }

    /*隐藏掉滚动条*/
  .overflowOpen::-webkit-scrollbar {
    display: none;
  }
}

// .img-list {
//   height: 166px;
//   overflow: hidden;
//   display: flex;
//   flex-direction: row;

//   /* 手指左右滑动 */
//   display: -webkit-box;
//   overflow-x: auto;
//   /*适应苹果*/
//   -webkit-overflow-scrolling: touch;
// }
// /*隐藏掉滚动条*/
// .img-list::-webkit-scrollbar {
//   display: none;
// }
.play-vd {
  position: fixed;
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, .7);

  >video {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
  }
}

</style>