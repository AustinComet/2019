<template>
  <div>
    <div class="spotlight-container card">
      <div
        v-for="(active, index) in actives"
        :key="index"
        class="spotlight card"
      >
        <div class="card-container">
          <div class="logo-image" :style="{ 'background-image': `url(/2019/static/img/active/${active.image})` }"></div>
          <div class="content">
            <h1>{{ active.name }}</h1>
            <p v-html="active.description.replace(/\|\|((?:http(s)?:\/\/)?[\w.-]+(?:\.[\w\.-]+)+[\w\-\._~:/?#[\]@!\$&'\(\)\*\+,;=.]+)\|+\|(.*)\|\|/gm, `<a href='$1' target='_blank' rel='noopener noreferrer'>$3</a>`)"></p>
          </div>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import * as Layout from '@/components'
import activeData from '../../static/json/active.json'

export default {
  components: {
    ...Layout
  },
  data () {
    return {
      actives: activeData
    }
  }
}
</script>

<style lang="scss" scoped>
.card-container {
  .logo-image {
    background-size: auto 200px !important;
    min-height: 350px;
    opacity: .5;

    @media screen and (max-width: 690px) {
      min-height: 200px;
    }
  }
}
</style>
