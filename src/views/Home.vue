<template>
  <div>
    <bounce-loader :loading="isLoading" :color="'#68d391'" :size="100" />
    <PxAssetsTable v-if="!isLoading" v-bind:assets="assets" />
  </div>
</template>

<script>
import PxAssetsTable from '@/components/PxAssetsTable'
import api from '@/api'

export default {
  name: 'Home',
  components: { PxAssetsTable },

  data() {
    return {
      isLoading: false,
      assets: []
    }
  },

  created() {
    this.isLoading = true

    api
      .getAssets()
      .then(assets => (this.assets = assets))
      .finally(() => (this.isLoading = false))
  }
}
</script>
