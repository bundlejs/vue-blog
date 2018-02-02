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
        <img class="personal-info-image-block" src="https://ss0.bdstatic.com/94oJfD_bAAcT8t7mm9GUKT-xh_/timg?image&quality=100&size=b4000_4000&sec=1517571092&di=85e62d80627d31b4ba2d299d7cdef4a4&src=http://img3.duitang.com/uploads/people/201609/11/20160911214236_xaizW.jpeg" alt="" @click="goTo($event)">
      </div>
    </div>
    <div style="width: 100%;display: flex;justify-content: center">
      <div style="width: 250px;height: 250px;border: 1px solid black">
        <canvas width="250px" height="250px" ref="screen" v-on="{ mousewheel: mousewheel, click: click, dblclick: dblclick, mousedown: mousedown, mouseup: mouseup, mouseover: mouseover, mouseout: mouseout, mousemove: mousemove, mouseenter: mouseenter, mouseleave: mouseleave }"></canvas>
      </div>
    </div>
    <!--<input v-model="point1" type="text">-->
    <!--<input v-model="point2" type="text">-->
    <div style="display:none;">
      <img id="source" src="http://img1.imgtn.bdimg.com/it/u=3300592090,3700440559&fm=27&gp=0.jpg" width="300" height="227" ref="img">
    </div>
    <!--https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/drawImage-->
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      screen: null,
      height: 200,
      width: 200,
      x: 0,
      y: 0,
      dragging: false
    }
  },
  mounted: function () {
    console.log(this.$refs.screen)
    this.screen = this.$refs.screen.getContext('2d')
    console.log(this.screen)
    this.screen.drawImage(this.$refs.img, this.x, this.y, this.width, this.height)
    this.screen.beginPath()
    this.screen.arc(this.x + this.width * 0.5, this.y + this.height * 0.5, 10, 0, 2 * Math.PI, false)
    this.screen.stroke()
    this.screen.beginPath()
    this.screen.arc(this.x + this.width * 0.3, this.y + this.height * 0.8, 10, 0, 2 * Math.PI, false)
    this.screen.stroke()
  },
  methods: {
    goTo: function (e) {
      console.log(e)
    },
    mousewheel: function (e) {
      this.width += this.width * e.wheelDelta / 1000
      this.height += this.height * e.wheelDelta / 1000
      this.x = e.offsetX - (e.offsetX - this.x) * (1 + e.wheelDelta / 1000)
      this.y = e.offsetY - (e.offsetY - this.y) * (1 + e.wheelDelta / 1000)
      this.screen.clearRect(0, 0, 250, 250)
      this.screen.drawImage(this.$refs.img, this.x, this.y, this.width, this.height)
      this.screen.beginPath()
      this.screen.arc(this.x + this.width * 0.5, this.y + this.height * 0.5, 10, 0, 2 * Math.PI, false)
      this.screen.stroke()
      this.screen.beginPath()
      this.screen.arc(this.x + this.width * 0.3, this.y + this.height * 0.8, 10, 0, 2 * Math.PI, false)
      this.screen.stroke()
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
      this.dragging = true
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
    },
    mouseup: function (e) {
      this.dragging = false
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
    },
    mouseover: function (e) {
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
    },
    mouseout: function (e) {
      this.dragging = false
      // console.log(e)
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
      this.screen.stroke()
    },
    mousemove: function (e) {
      if (this.dragging) {
        this.x += e.movementX
        this.y += e.movementY
        this.screen.clearRect(0, 0, 250, 250)
        this.screen.drawImage(this.$refs.img, this.x, this.y, this.width, this.height)
        this.screen.beginPath()
        this.screen.arc(this.x + this.width * 0.5, this.y + this.height * 0.5, 10, 0, 2 * Math.PI, false)
        this.screen.stroke()
        this.screen.beginPath()
        this.screen.arc(this.x + this.width * 0.3, this.y + this.height * 0.8, 10, 0, 2 * Math.PI, false)
        this.screen.stroke()
      }
      // console.log('canvas坐标:', e.offsetX, ',', e.offsetY)
      // this.point1 = e.offsetX
      // this.point2 = e.offsetY
    },
    mouseenter: function (e) {
      // this.screen.beginPath()
      // this.screen.lineWidth = '1'
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
