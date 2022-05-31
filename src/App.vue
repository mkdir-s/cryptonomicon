<template>
  <div class="container">
    <h2 class="title">Тикер</h2>
    <input
      class="input"
      type="text"
      placeholder="Например DOGE"
      v-model="ticker"
      @keydown.enter="addTicker"
    />
    <button class="button" @click="addTicker">+ Добавить</button>
    <template v-if="tickers.length > 0">
      <hr class="hr" />
      <div class="items">
        <div class="item" v-for="t in tickers" :key="t.name" @click="sel = t">
          <h4 class="item__title">{{ t.name }} - USD</h4>
          <h3 class="item__price">{{ t.price }}</h3>
          <button class="item__button" @click="handleDelete(t)">
            - Удалить
          </button>
        </div>
      </div>
      <hr class="hr" />
    </template>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      ticker: null,
      tickers: [
        { name: "DEMO1", price: "-" },
        { name: "DEMO2", price: "-" },
        { name: "DEMO3", price: "-" },
        { name: "DEMO4", price: "-" },
      ],
    };
  },
  methods: {
    addTicker() {
      const newTicker = {
        name: this.ticker.toUpperCase(),
        price: "-",
      };
      this.tickers.push(newTicker);
      this.ticker = "";
    },
    handleDelete(tickersToRemove) {
      this.tickers = this.tickers.filter((t) => t != tickersToRemove);
    },
  },
};
</script>

<style src="./app.css"></style>
