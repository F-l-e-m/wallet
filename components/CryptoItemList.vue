<template>
  <div class="crypto-item-list">
    <template v-if="isAuth">
      <div class="balance">
        <p class="balance__title">Общий баланс</p>
        <p class="balance__value">{{ balance }}$</p>
      </div>
      <ul class="crypto-item-list__items">
        <li
          v-for="wallet in wallets"
          :key="wallet.id"
          class="crypto-item-list__items-wrapper"
        >
          <CryptoItem
            :balance="wallet.balance"
            :description="wallet.description"
            :title="wallet.title"
            :slug="wallet.slug"
          />
        </li>
      </ul>
    </template>
    <template v-else>
      <h1 class="crypto-item-list__error">Авторизуйтесь</h1>
    </template>
  </div>
</template>

<script>
import CryptoItem from '@/components/CryptoItem'
export default {
  name: 'CryptoItemList',
  components: {
    CryptoItem,
  },
  data() {
    return {
      isAuth: false,
      wallets: [],
      balance: 0,
    }
  },
  async mounted() {
    const headers = {
      headers: {
        Authorization: `Bearer ${localStorage.getItem('token')}`,
      },
    }
    await this.$axios
      .$get('http://80.87.192.59:5252/api/wallet', headers)
      .then(({ balance, wallets }) => {
        this.isAuth = true
        this.wallets = wallets
        this.balance = balance
      })
      .catch(() => {
        this.isAuth = false
      })
  },
}
</script>

<style scoped>
.crypto-item-list__items {
  list-style: none;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
}

.balance {
  margin-bottom: 28px;
}

.balance__title {
  color: #fff;
  font-size: 11px;
  line-height: 16px;
}

.balance__value {
  font-weight: bold;
  font-size: 18px;
  line-height: 21px;
  background: linear-gradient(90deg, #ff0099 0%, #5131e4 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.crypto-item-list__items-wrapper {
  margin-right: 16px;
  margin-top: 16px;
}

.crypto-item-list__items-wrapper:last-child {
  margin-right: 0;
}

.crypto-item-list__error {
  color: #fff;
}
</style>
