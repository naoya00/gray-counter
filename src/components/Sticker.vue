<template>
  <div class="stickerLow">
    <div class="stickerLow__title">{{ title }}</div>
    <div class="stickerLow__contents">
      <span class="stickerLow__contents--value">{{ value }}</span>
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

<style lang="scss" scoped>
.stickerLow{
  margin: 20px;
  border: 1px solid black;
  border-radius: 5px;
  &__title{
    font-weight: bold;
    margin: 10px 0 0 5px;
  }
  &__contents{
    text-align: center;
    margin: 20px 0;
    &--value{
      font-size: 2.5em;
      margin-right: 5px;
    }
    }
}

</style>