<template>
  <div class="hello">
    <div class="personal-info">
      <div class="personal-info-message">
        <div class="name">BundleJs</div>
        <div class="description">Programmer Designer</div>
        <div class="address">
          <div class="address-icon">
            <icon name="location" scale="1.6"></icon>
          </div>
          <div class="address-detail">China Dalian</div>
        </div>
        <div class="detail">
          <div class="detail-item">
            <div class="detail-item-message">14</div>
            <div class="detail-item-title">Live</div>
          </div>
          <div class="detail-item">
            <div class="detail-item-message">23</div>
            <div class="detail-item-title">Done</div>
          </div>
        </div>
      </div>
      <div class="personal-info-image">
        <img class="personal-info-image-block" src="http://172.16.72.12:8000/3.png" alt="" @click="goTo($event)">
      </div>
    </div>
    <div style="width: 100%;display: flex;justify-content: center">
      <div style="width: 250px;height: 250px;border: 1px solid black">
        <canvas width="250px" height="250px" ref="screen" v-on="{ mousewheel: mousewheel, click: click, dblclick: dblclick, mousedown: mousedown, mouseup: mouseup, mouseover: mouseover, mouseout: mouseout, mousemove: mousemove, mouseenter: mouseenter, mouseleave: mouseleave }"></canvas>
      </div>
    </div>
    <input v-model="point1" type="text">
    <input v-model="point2" type="text">
    <div style="display:none;">
      <img id="source" src="https://mdn.mozillademos.org/files/5397/rhino.jpg" width="300" height="227" ref="img">
    </div>
    https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/drawImage
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      screen: null,
      point1: 0,
      point2: 0
    }
  },
  mounted: function () {
    console.log(this.$refs.screen)
    this.screen = this.$refs.screen.getContext("2d")
    console.log(this.screen)
    this.screen.drawImage(this.$refs.img, 0,0)
  },
  methods: {
    goTo: function (e) {
      console.log(e)
    },
    mousewheel: function (e) {
      console.log(e)
      console.log('canvas坐标:', e.offsetX, ',', e.offsetX)
    },
    click: function (e) {
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
    },
    dblclick: function (e) {
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
    },
    mousedown: function (e) {
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
    },
    mouseup: function (e) {
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
    },
    mouseover: function (e) {
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
    },
    mouseout: function (e) {
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
      this.screen.stroke()
    },
    mousemove: function (e) {
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
      this.point1 = e.offsetX;
      this.point2 = e.offsetY;
//      this.screen.lineTo(e.offsetX, e.offsetY);
//      this.screen.stroke()
//      this.screen.moveTo(e.offsetX,e.offsetY);
    },
    mouseenter: function (e) {
      this.screen.beginPath();
      this.screen.lineWidth = '1'
//      this.screen.moveTo(e.offsetX*1.2,e.offsetY*0.6);
      this.screen.moveTo(e.offsetX,e.offsetY);
//       console.log(this)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetX)
    },
    mouseleave: function (e) {
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetX)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .personal-info {
    color: #544040;
    display: flex;
  }

  .personal-info-message {
    flex: 1;
    padding: 30px 0 0 50px;
  }

  .name {
    font-size: 22px;
    font-weight: 900;
  }

  .description {
    font-size: 14px;
    padding: 5px 0 0 0;
    min-height: 50px;
    color: #5B4848;
  }

  .address {
    display: flex;
    color: #A59A9A;
    padding-top: 10px;
  }

  .address-detail {
    font-size: 14px;
    font-weight: 500;
    display: flex;
    align-items: flex-end;
  }

  .address-icon {
    width: 25px;
    /*height: 20px;*/
  }

  .detail {
    display: flex;
  }

  .detail-item {
    width: 60px;
    font-size: 15px;
    padding-top: 16px;
  }

  .detail-item-message {
    font-weight: bold;
  }

  .detail-item-title {
    color: #A59A9A;
    font-size: 13px;
    font-weight: 500;
  }

  .personal-info-image {
    width: 180px;
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding-top: 8px;
  }

  .personal-info-image-block {
    display: block;
    width: 110px;
    height: 150px;
    box-shadow: 0 8px 25px 0 rgba(84, 64, 64, 0.2);
    border: 3px solid white;
    border-radius: 7px;
    object-fit: cover;
  }

</style>
