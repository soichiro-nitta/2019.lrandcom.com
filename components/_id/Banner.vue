<template>
  <div class="Banner">
    <BannerItemNew
      v-if="num === 1"
      :num="num"
      :to="insta"
      head="インスタ毎日更新中！!"
      body="iPhone時代だからこそ、何を撮るかが問われる。その人にしか美しく見えないもの。"
      button="Instagramをみる"
      @increment="increment"
    />
    <!-- <BannerItemNuxt
      v-if="num === 2"
      :num="num"
      to="/writer"
      head="ライター募集中！!"
      body="書き手がつまらないと感じたら、読み手はその10倍はつまらないよね。"
      button="詳細をみる"
      @increment="increment"
    /> -->
  </div>
</template>

<script>
import URL from '~/assets/data/url.json'
import BannerItemNew from './BannerItemNew'
// import BannerItemNuxt from './BannerItemNuxt'

export default {
  components: {
    BannerItemNew
    // BannerItemNuxt
  },
  data() {
    return {
      insta: URL.INSTA,
      num: 1
    }
  },
  mounted() {
    // localStorage['lrandcom.com'].banner.insta = 'true'
  },
  methods: {
    async increment() {
      await this.$delay(700)
      this.num++
    }
  }
}
</script>
