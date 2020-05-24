<template>
  <div class="p-6 justify-center text-center overflow-auto">
    <logo />
    <div v-if="!this.$auth.loggedIn">
      <h1 class="text-4xl">
        nuxt-auth-azuread-example
      </h1>
      <a class="tracking-tight cursor-pointer" @click="$auth.loginWith('aad')">Sign in with Microsoft</a>
    </div>
    <div v-else="">
      <h1 class="text-4xl">
        Hi, {{ jwt_decoded.given_name }}
      </h1>
      <hr class="m-6">
      <code><strong>Decoded JWT:</strong> {{ jwt_decoded }}</code>
    </div>
  </div>
</template>

<script lang="ts">
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  asyncData (context: any) {
    return {
      jwt_decoded: context.app.$auth.$storage.getUniversal('jwt_decoded')
    }
  },
  data () {
    return { jwt_decoded: null }
  }
}
</script>
