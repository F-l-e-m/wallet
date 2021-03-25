<template>
  <div class="auth">
    <Input v-model="email" placeholder="Email" class="auth__input" />
    <Input
      v-model="password"
      :placeholder="$t('placeholderPassword')"
      class="auth__input"
    />
    <Button text="Авторизация" class="auth__btn" @click="auth" />
  </div>
</template>

<script>
import Input from '@/components/input.vue'
import Button from '@/components/button.vue'
import { mapMutations } from 'vuex'
export default {
  name: 'Auth',
  components: {
    Button,
    Input,
  },
  data() {
    return {
      email: '',
      password: '',
      isAuth: false,
    }
  },
  methods: {
    ...mapMutations(['addToken']),
    async auth() {
      await this.$axios
        .$post('http://80.87.192.59:5252/api/auth/login', {
          email: this.email,
          password: this.password,
        })
        .then((data) => {
          localStorage.setItem('token', data.access_token)
          this.isAuth = true
        })
        .catch(() => {
          this.isAuth = false
          this.email = ''
          this.password = ''
        })
    },
  },
}
</script>

<style scoped>
.auth {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.auth__input {
  margin-bottom: 18px;
}

.auth__input:last-child {
  margin-bottom: 0;
}

.auth__btn {
  margin-top: 30px;
}
</style>
