<template>
  <div class="frame">
    <div class="custmersLow">
      <div class="title">本日の総客・指名率</div>

      <Sticker 
        :title="'総客'"
        :unit="'人'"
        :value="customers + appointedCustomers" />

      <Sticker 
        :title="'指名率'"
        :unit="'％'"
        :value="nominationRate" />

      <Counter 
        :title="'指名なし'"
        :unit="'人'"
        :varName="'customers'"
        @updated="commit"
      />

      <Counter 
        :title="'指名あり'"
        :unit="'人'"
        :varName="'appointedCustomers'"
        @updated="commit"
      />

    </div>

    <div class="grayLow">

    <div class="title">本日のグレイカラー率</div>

    <Sticker 
      :title="'カラー施術人数'"
      :unit="'人'"
      :value="good + bad" />

    <Sticker 
      :title="'グレイ率（白髪染め）'"
      :unit="'％'"
      :value="defectivePercent" />

    <Counter 
      :title="'ファッションカラー（おしゃれ染め）'"
      :unit="'人'"
      :varName="'good'"
      @updated="commit"
    />

    <Counter 
      :title="'グレイカラー（白髪染め）'"
      :unit="'人'"
      :varName="'bad'"
      @updated="commit"
    />

    </div>
  </div>
</template>

<script>
import Sticker from './components/Sticker.vue'
import Counter from './components/Counter.vue'
export default {
  components: {
    Sticker,
    Counter
  },
  data () {
    return {
      good: 0,
      bad: 0,
      customers: 0,
      appointedCustomers:0
    }
  },
  computed: {
    defectivePercent () {
      return Number((this.bad / (this.good + this.bad) * 100).toFixed(2)) || 0
    },
    nominationRate () {
      return Number((this.appointedCustomers / (this.customers + this.appointedCustomers) * 100).toFixed(2)) || 0
    }
  },
  methods: {
    commit (newValue, variable) {
      this[variable] = newValue
    }
  }
}
</script>

<style lang="scss">
.UI_Build_Assistant{
  margin: 0;
}
.frame{
  display: flex;
  height: 100vh;
  width: 100%;
}

</style>