<template>
  <div class="crypto-item">
    <div class="crypto-item__header">
      <cryptoicon :symbol="slug" />
      <h2 class="crypto-item__title">{{ title.toUpperCase() }}</h2>
    </div>
    <div class="crypto-item__info">
      {{ parsedBalance }}
    </div>
    <div class="crypto-item__controllers">
      <button class="crypto-item__controllers-item">Получить</button>
      <button
        class="crypto-item__controllers-item crypto-item__controllers-item--white"
      >
        Отправить
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CryptoItem',
  props: {
    balance: {
      type: Number,
      default: 0,
    },
    description: {
      type: String,
      default: '',
    },
    slug: {
      type: String,
      default: '',
    },
    title: {
      type: String,
      required: true,
    },
  },
  computed: {
    parsedBalance() {
      return this.balance + ' ' + this.slug.toUpperCase()
    },
  },
}
</script>

<style scoped>
.crypto-item {
  padding: 12px 12px 14px 14px;
  background: linear-gradient(241.43deg, #3b37f1 0%, #ff007d 100%);
  border-radius: 10px;
  width: 256px;
}

.crypto-item__header {
  display: flex;
  align-items: center;
  margin-bottom: 12px;
}

.crypto-item__title {
  color: #fff;
  font-size: 13px;
  line-height: 16px;
  font-weight: 400;
  margin-left: 8px;
}

.crypto-item__info {
  color: #fff;
  font-size: 18px;
  line-height: 21px;
  font-weight: 700;
  margin-bottom: 33px;
}

.crypto-item__controllers-item {
  margin-right: 11px;
  padding: 6px 16px;
  background: transparent;
  border: 1px solid #ffffff;
  border-radius: 10px;
  font-size: 9px;
  color: #fff;
  cursor: pointer;
}

.crypto-item__controllers-item:last-child {
  margin-right: 0;
}

.crypto-item__controllers-item--white {
  background: #fff;
  color: #1c1c1c;
}
</style>
