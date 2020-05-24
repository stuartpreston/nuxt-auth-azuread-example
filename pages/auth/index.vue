<template>
  <div />
</template>

<script lang="ts">
// eslint-disable-next-line camelcase
import jwt_decode from 'jwt-decode'

export default {
  created () {
    const decodedBearer = jwt_decode(this.$auth.$storage.getUniversal('_token.aad'))
    this.$auth.$storage.setUniversal('jwt_decoded', decodedBearer)
  }
}
</script>
