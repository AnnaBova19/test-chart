<template>
  <div>
    <timeline></timeline>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import Timeline from '@/components/Timeline.vue'

@Component({
  components: {
    Timeline,
  },
})
export default class Home extends Vue {}
</script>
