<template>
  <!-- <view>
    123
    <view style="width: 100%; height: 500rpx"><l-f2 ref="chart"></l-f2></view>
  </view> -->
  <view class="f2-chart">
    <f2 onInit="onInitChart"></f2>
    <custom-chart />
  </view>
</template>

<script>
// import F2 from '@/uni_modules/lime-f2/components/l-f2/f2.min.js'
export default {
  data() {
    return {
      title: 'Hello',
      baseData: [
        { genre: '成犬粮', sold: 275 },
        { genre: '化毛膏', sold: 115 },
        { genre: '益生菌', sold: 120 },
        { genre: '氨糖', sold: 350 },
        { genre: '其它', sold: 150 },
      ],
    }
  },
  // mounted() {
  //   this.$refs.chart.init((config) => {
  //     console.log('1111111111', config)
  //     const chart = new F2.Chart(config)
  //     chart.source(this.baseData)
  //     chart.interval().position('genre*sold').color('genre')
  //     chart.render()
  //     // 需要把 chart 返回
  //     return chart
  //   })
  // },
  onLoad() {
    // console.log('load')
    // this.$refs.chart.init((config) => {
    //   console.log('1111111111', config)
    //   const chart = new F2.Chart(config)
    //   chart.source(this.baseData)
    //   chart.interval().position('genre*sold').color('genre')
    //   chart.render()
    //   // 需要把 chart 返回
    //   return chart
    // })
  },
  methods: {
    handleClick() {},
    onInitChart(F2, config) {
      console.log('1111111111', F2)
      const chart = new F2.Chart(config)
      const data = [
        { value: 63.4, city: 'New York', date: '2011-10-01' },
        { value: 62.7, city: 'Alaska', date: '2011-10-01' },
        { value: 72.2, city: 'Austin', date: '2011-10-01' },
        { value: 58, city: 'New York', date: '2011-10-02' },
        { value: 59.9, city: 'Alaska', date: '2011-10-02' },
        { value: 67.7, city: 'Austin', date: '2011-10-02' },
        { value: 53.3, city: 'New York', date: '2011-10-03' },
        { value: 59.1, city: 'Alaska', date: '2011-10-03' },
        { value: 69.4, city: 'Austin', date: '2011-10-03' },
      ]
      chart.source(data, {
        date: {
          range: [0, 1],
          type: 'timeCat',
          mask: 'MM-DD',
        },
        value: {
          max: 300,
          tickCount: 4,
        },
      })
      chart.area().position('date*value').color('city').adjust('stack')
      chart.line().position('date*value').color('city').adjust('stack')
      chart.render()
      // 注意：需要把chart return 出来
      return chart
    },
  },
}
</script>

<style>
.f2-chart {
  width: 740rpx;
  height: 500rpx;
  border: 2px solid pink;
}
</style>
