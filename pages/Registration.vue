<template>
  <div class="registration">
    <Input v-model="name" placeholder="Имя" class="registration__input" />
    <Input v-model="email" placeholder="Email" class="registration__input" />
    <Input
      v-model="password"
      placeholder="Password"
      class="registration__input"
    />
    <Button
      text="Регистрация"
      class="registration__btn"
      @click="registration"
    />
  </div>
</template>

<script>
import Input from '@/components/input.vue'
import Button from '@/components/button.vue'
export default {
  name: 'Registration',
  components: {
    Input,
    Button,
  },
  data() {
    return {
      name: '',
      email: '',
      password: '',
    }
  },
  methods: {
    async registration() {
      await this.$axios
        .$post('http://80.87.192.59:5252/api/auth/register', {
          name: this.name,
          email: this.email,
          password: this.password,
        })
        .then(async (data) => {
          await this.$axios
            .$post('http://80.87.192.59:5252/api/auth/login', {
              email: this.email,
              password: this.password,
            })
            .then((data) => {
              localStorage.setItem('token', data.access_token)
              this.isAuth = true
              this.$router.push('/')
            })
            .catch(() => {
              this.isAuth = false
              this.email = ''
              this.password = ''
            })
        })
        .catch(() => {
          this.name = ''
          this.email = ''
          this.password = ''
        })
    },
  },
}
</script>

<style scoped>
.registration {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.registration__input {
  margin-bottom: 18px;
}

.registration__input:last-child {
  margin-bottom: 0;
}

.registration__btn {
  margin-top: 30px;
}
</style>
