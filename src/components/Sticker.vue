<template>
  <div class="item">
    <h2>{{ title }}</h2>
    <p>
      <span class="value">{{ value }}</span>
      <span class="unit">[ {{ unit }} ]</span>
    </p>
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