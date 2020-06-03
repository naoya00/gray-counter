<template>
<div class="item">
    <Sticker
      :title="title"
      :unit="unit"
      :value="value"
    />
    <div class="counterLow">
      <button class="add-button"
        @click="plusOne">追加</button>
    </div>
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

<style lang="scss" scoped>
.counterLow{
  text-align: center
}
.add-button {
  position: relative;
  display: inline-block;
  font-weight: bold;
  text-decoration: none;
  color: #FFF;
  text-shadow: 0 0 5px rgba(255, 255, 255, 0.73);
  padding: 0.3em 0.5em;
  background: #00bcd4;
  border-top: solid 3px #00a3d4;
  border-bottom: solid 3px #00a3d4;
  transition: .4s;
  cursor: pointer;
  width: 30%;
  outline: none;
  &:hover {
  text-shadow: -6px 0px 15px rgba(255, 255, 240, 0.83),
                6px 0px 15px rgba(255, 255, 240, 0.83);
  }
}

</style>