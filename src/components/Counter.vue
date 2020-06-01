<template>
<div class="item">
    <Sticker
      :title="title"
      :unit="unit"
      :value="value"
    />
    <button class="add-button"
      @click="plusOne">追加</button>
  </div>
</template>

<script>
import Sticker from './Sticker.vue'
export default {
  components: {
    Sticker
  },
  props: {
    title: {
      type: String
    },
    unit: {
      type: String
    },
    varName: {
      type: String
    }
  },
  data () {
    return {
      value: 0
    }
  },
  methods: {
    plusOne () {
      this.value += 1
      this.$emit('updated', this.value, this.varName)
    }
  }
}
</script>