<template>
  <div class="banner">
    <div class="box">
      <div class="left">
        <img class="banner1" src="../views/../assets/img/banner1.png"/>
        <div class="bott">
          <p class="bott1" @click="leaveFor('')">
            <!-- <img src="../views/assets/1.svg" /> -->
            <img src="../views/../assets/img/1.svg" />
            学术交流服务平台
          </p>
          <p class="bott2" @click="leaveFor('')">
            <img src="../views/../assets/img/2.svg" />继续医学教育平台
          </p>
          <div class="erweimaBox">
            <div class="erweima">
              <img src="../views/../assets/img/erweima.png"/>
              <p>医学会公众号</p>
            </div>
            <div class="erweima">
              <img src="../views/../assets/img/erweima.png"/>
              <p>医师协会公众号</p>
            </div>
          </div>
          <p class="botmP">备案号：豫ICP备05017677号</p>
        </div>
      </div>
      <div class="right">
        <div class="way" @click="leaveFor('https://www.henanyixue.com/#/')">
          <img src="../views/../assets/img/banner3.png" />
        </div>
        <div class="way" @click="leaveFor('')">
          <img src="../views/../assets/img/banner2.png" />
        </div>
        <div class="way" @click="leaveFor()">
          <img src="../views/../assets/img/banner4.png" />
        </div>
      </div>
      
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  methods: {
    leaveFor(url) {
      if (url) {
        window.open(url);
      } else {
        // console.log("前往建设中网页");
        this.$router.push({
          path:'/error'
        })
      }
    },
  },
};
</script>
<style lang="scss">
html,
body,
#app,
.banner {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
.banner {
  background-image: url("../views/../assets/img/1689216752944.png");
  background-repeat: no-repeat;
  background-size: 100% 100%;
  .box {
    width: 80%;
    // height: 70%;
    height: 80%;
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    right: 0;
    margin: auto;
    display: flex;
    justify-content: space-between;
    .left {
      background-color: #000000b2;
      width: 25%;
      overflow: auto;
      .banner1 {
        width: 100%;
      }
      .bott {
        width: 60%;
        padding: 40px 30px;
        margin: 0 auto;
      }
      .bott1,
      .bott2 {
        height: 45px;
        background-color: #30c2ca;
        display: flex;
        align-items: center;
        border-radius: 10px;
        padding: 10px 20px;
        color: white;
        font-weight: 700;
        white-space: nowrap;
        cursor: pointer;
        img {
          width: 35px;
          height: 35px;
          margin-right: 10px;
        }
      }
      .erweimaBox {
        display: flex;
        justify-content: space-between;
        .erweima {
          width: 48%;
          display: flex;
          flex-direction: column;
          p {
            padding: 5px 0;
            margin: 0;
            width: 100%;
            border-radius: 0 0 10px 10px;
            background-color: #637174;
            text-align: center;
            color: white;
            font-size: 12px;
          }
          img {
            width: 100%;
            border-radius: 10px 10px 0 0;
          }
        }
      }
      .botmP {
        padding: 10px 0;
        margin: 15px 0 0;
        width: 100%;
        border-radius: 10px;
        background-color: #637174;
        text-align: center;
        color: white;
        font-size: 12px;
      }
    }
    .right {
      width: 65%;
      display: flex;
      // align-items: flex-end;
      position: absolute;
      // left:30%;
      right:0;
      bottom:0;
      animation-name: example;
      animation-duration: 1s;
      .way {
        flex: 1;
        height: 30vh;
        margin: 0 3px;
        border-radius: 10px;
        background-color: #000000b2;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        img {
          width: 60%;
          height: 60%;
        }
      }
    }
  }
}
@keyframes example {
  0%   { right:0px; bottom:-500px;}
  // 25%  {background-color:yellow; right:200px; top:0px;}
  // 50%  {background-color:blue; left:200px; top:200px;}
  // 75%  {background-color:green; left:0px; top:200px;}
  100% { right:0px; bottom:0px;}
}
</style>
