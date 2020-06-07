<template>
  <Contributors type="opencollective-backers" :contributors="sponsors"></Contributors>
</template>
<script>
  import { getSponsors } from '@tsed/vuepress-common'
  import Contributors from '../contributors/Contributors.vue'

  export default {
    name: 'OpenCollectiveSponsors',
    data: () => {
      return {
        sponsors: []
      }
    },

    components: {
      Contributors
    },

    async mounted () {
      const {
        openCollective
      } = this.$site.themeConfig

      this.sponsors = await getSponsors(openCollective)
    }
  }
</script>
