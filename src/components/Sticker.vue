<template>
  <div class="item">
    <div>{{ title }}</div>
    <div>
      <span class="value">{{ value }}</span>
      <span class="unit">[ {{ unit }} ]</span>
    </div>
  </div>
</template>

<script>
export default {
    props: {
    title: {
      type: String
    },
    value: {
      type: Number,
      default: 0
    },
    unit: {
      type: String
    }
  }
}
</script>