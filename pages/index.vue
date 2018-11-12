<template>
  <section class="container">
    <Map />

    <div
      class="container"
      style="color: #fff;">
      <p>&nbsp;</p>
      <p>Content here</p>

      {{ message }}
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Map from '~/components/Map.vue'

export default {
  components: {
    Logo,
    Map
  },
  data: () => ({
    message: 'foi'
  })
}
</script>
