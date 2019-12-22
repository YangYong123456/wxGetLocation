<template>
  <div>
    <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
    >
      <block v-for="img in imgUrls" :key="img">
        <swiper-item>
          <image :src="img" style="width:100%" />
        </swiper-item>
      </block>
    </swiper>
    <i-grid i-class="no-border">
    <i-grid-item @click="goType(grid)" v-for="grid in grids" :key="grid" i-class="no-border">
        <i-grid-icon>
            <image :src="grid.image" />
        </i-grid-icon>
        <i-grid-label>{{grid.title}}</i-grid-label>
    </i-grid-item>
    </i-grid>
    <i-panel :title="title_name">
      <view style="padding: 15px;">
        <i-card v-for="item in top" :key="item" i-class="split" :extra="item.name" :thumb="item.image">
            <view slot="content">{{item.remark}}</view>
            <view slot="footer">{{item.address}}</view>
        </i-card>
      </view>
    </i-panel>
  </div>
</template>

<script>


export default {
  data () {
    return {
      title_name: "热门",
      grids:[
        {title:"饮品",image:"/static/images/1.png"},
        {title:"主食",image:"/static/images/2.png"},
        {title:"零食",image:"/static/images/3.png"},
        {title:"外卖",image:"/static/images/4.png"}
      ],
      top:[
        {name:"coco都可",address:"湖北大学正门对面",image:"/static/images/coco都可.jpg",remark:"很好喝"},
        {name:"N多寿司",address:"湖北大学正门对面",image:"/static/images/N多寿司.jpg",remark:"很好吃，价格适中"},
        {name:"热干面",address:"湖北大学食堂",image:"/static/images/热干面.jpg",remark:"武汉特产，价格便宜"},
        {name:"良品铺子",address:"湖大夜市旁边",image:"/static/images/良品铺子.jpg",remark:"价格较贵，但是好吃"}
      ],
      imgUrls: [
        '/static/images/大盘鸡.jpg',
        '/static/images/蛋糕.jpg',
        '/static/images/西餐.jpg'
      ],
      indicatorDots: false,
      autoplay: false,
      interval: 5000,
      duration: 1000
    }
  },

  

  methods: { 
    goType(type){
      console.log(type)
      let url = '../list/main?type=' + type.title
      mpvue.navigateTo({ url })
    }
  },

  created () {
  }
}
</script>

<style scoped>
div >>> .no-border {
  border-width: 0pt;
}
div >>> .split {
  margin-bottom: 10pt;
}
</style>

