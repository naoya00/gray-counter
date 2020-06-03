<template>
  <div class="frame">
    <div class="contentLow">
      <div class="title">本日の総客・指名率</div>

      <Sticker 
        :title="'総客'"
        :unit="'人'"
        :value="customers + appointedCustomers"
        />

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

    <div class="contentLow">

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

    <div class="contentLow">

      <div class="title">オプションメニュー</div>

      <Sticker 
      :title="'パーマ施術率'"
      :unit="'%'"
      :value="permTreatmentRate" />

      <Sticker 
      :title="'トリートメント施術率'"
      :unit="'%'"
      :value="treatmentTreatmentRate" />

      <Counter 
        :title="'パーマ施術人数'"
        :unit="'人'"
        :varName="'perm'"
        @updated="commit"
      />

      <Counter 
        :title="'トリートメント施術人数'"
        :unit="'人'"
        :varName="'treatment'"
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
      appointedCustomers:0,
      perm:0,
      treatment: 0
    }
  },
  computed: {
    defectivePercent () {
      return Number((this.bad / (this.good + this.bad) * 100).toFixed(2)) || 0
    },
    nominationRate () {
      return Number((this.appointedCustomers / (this.customers + this.appointedCustomers) * 100).toFixed(2)) || 0
    },
    permTreatmentRate () {
      return Number((this.perm / (this.customers + this.perm) * 100).toFixed(2)) || 0
    },
    treatmentTreatmentRate () {
      return Number((this.treatment / (this.customers + this.treatment) * 100).toFixed(2)) || 0
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
  justify-content: space-between;
  height: calc(100vh - 200px);
  width: 80%;
  margin: 100px auto;
}
.contentLow{
  width: 32%;
  background-color: #F5F5F5;
}
.title{
  background-color: 	#D2B48C;
  padding: 10px 0;
  text-align: center;
}
</style>