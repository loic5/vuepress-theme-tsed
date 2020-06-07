<template>
  <Contributors type="opencollective-backers" :contributors="backers"></Contributors>
</template>
<script>
  import { getBackers } from '@tsed/vuepress-common'
  import Contributors from '../contributors/Contributors.vue'

  export default {
    name: 'OpenCollectiveBackers',
    data: () => {
      return {
        backers: []
      }
    },

    components: {
      Contributors
    },

    async mounted () {
      const {
        openCollective
      } = this.$site.themeConfig

      this.backers = await getBackers(openCollective)
    }
  }
</script>
