<template>
  <div class="container">
    <x-header style="background-color:#1D62F0 " :right-options="{showMore: true}" @on-click-more="Login" :left-options="{showBack: false}">我爱读书</x-header>
    <swiper loop auto :list="img_list" :index="img_index"></swiper>
    <grid :cols="4" :show-lr-borders="false">
      <grid-item :label="('Grid')" v-for="i in 8" :key="i">
        <img slot="icon" src="../assets/grid_icon.png">
      </grid-item>
    </grid>
    <panel :header="'推荐'" :footer="footer" :list="list" :type="type"></panel>
    <tabbar>
      <tabbar-item>
        <img slot="icon" src="../assets/home.png">
        <span slot="label">首页</span>
      </tabbar-item>
      <tabbar-item show-dot>
        <img slot="icon" src="../assets/book.png">
        <span slot="label">书籍</span>
      </tabbar-item>
      <tabbar-item selected link="/now">
        <img slot="icon" src="../assets/map.png">
        <span slot="label">周边</span>
      </tabbar-item>
      <tabbar-item badge="2">
        <img slot="icon" src="../assets/mine.png">
        <span slot="label">我的</span>
      </tabbar-item>
    </tabbar>
    
  </div>
</template>

<script>
import { Tabbar, TabbarItem, Group, Cell, XHeader, Grid, GridItem, Swiper, Panel } from 'vux'

const baseList = [{
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vvsr72j20p00gogo2.jpg',
  title: '送你一朵fua'
}, {
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg',
  title: '送你一辆车'
}, {
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg',
  title: '送你一次旅行',
  fallbackImg: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw50iwj20ff0aaaci.jpg'
}]

const urlList = baseList.map((item, index) => ({
  url: 'http://m.baidu.com',
  img: item.img,
  fallbackImg: item.fallbackImg,
  title: `(可点击)${item.title}`
}))

export default {
  components: {
    Panel,
    XHeader,
    Tabbar,
    TabbarItem,
    Group,
    Cell,
    Grid,
    GridItem,
    Swiper
  },
  methods: {
    Login () {
      this.$router.push('/Login')
    }
  },
  created () {
    let _this = this
    this.$http.post('https://api.apiopen.top/getJoke').then(({data}) => {
      console.log(data)
      var newData = data.result.map((item, index) => ({
        src: item.header,
        fallbackSrc: item.header,
        title: item.name,
        desc: item.text
      }))
      console.log(newData)
      _this.list = newData
    })
  },
  data () {
    return {
      img_list: urlList,
      img_index: 0,
      msg: 'Hello World!',
      type: '1',
      list: [{
        src: 'http://www.zhantengwang.com/uploads/allimg/181016/1-1Q016144920196.jpg',
        fallbackSrc: 'http://placeholder.qiniudn.com/60x60/3cc51f/ffffff',
        title: '标题一',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: '/component/cell'
      }, {
        src: 'http://www.zhantengwang.com/uploads/allimg/181016/1-1Q016144920196.jpg',
        fallbackSrc: 'http://placeholder.qiniudn.com/60x60/3cc51f/ffffff',
        title: '标题一',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: '/component/cell'
      }, {
        src: 'http://www.zhantengwang.com/uploads/allimg/181016/1-1Q016144920196.jpg',
        fallbackSrc: 'http://placeholder.qiniudn.com/60x60/3cc51f/ffffff',
        title: '标题一',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: '/component/cell'
      }, {
        src: 'http://www.zhantengwang.com/uploads/allimg/181016/1-1Q016144920196.jpg',
        title: '标题二',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: {
          path: '/component/radio',
          replace: false
        },
        meta: {
          source: '来源信息',
          date: '时间',
          other: '其他信息'
          // iconType: '',
        }
      }],
      footer: {
        title: '更多',
        url: 'http://vux.li'
      }
    }
  }
}
</script>

<style>
.container /deep/ .weui-tabbar {
  position: fixed;
}
</style>
