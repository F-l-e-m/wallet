<template>
  <header class="header">
    <img src="@/assets/BIGWALLET.svg" alt="bigwallet logo" />
    <menu class="menu">
      <li class="menu__item">
        <nuxt-link to="/" class="menu__item-link">Кошельки</nuxt-link>
      </li>
      <li class="menu__item">
        <nuxt-link to="/auth" class="menu__item-link">Вход</nuxt-link>
      </li>
      <li class="menu__item">
        <nuxt-link to="/registration" class="menu__item-link"
          >Регистрация</nuxt-link
        >
      </li>
    </menu>
    <ul class="locale-block">
      <li class="locale-block__item">
        <nuxt-link :to="switchLocalePath('ru')">ru</nuxt-link>
      </li>
      <li class="locale-block__item">
        <nuxt-link :to="switchLocalePath('en')">en</nuxt-link>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  margin-bottom: 34px;
}

.menu {
  display: flex;
  list-style: none;
  margin-left: auto;
}

.menu__item {
  margin-right: 18px;
}

.menu__item:last-child {
  margin-right: 0;
}

.menu__item-link {
  text-decoration: none;
  font-size: 18px;
  font-weight: 300;
  color: #fff;
}

.locale-block {
  list-style: none;
  display: flex;
}

.locale-block__item {
  margin-right: 10px;
}

.locale-block__item a {
  color: #fff;
  font-size: 18px;
  text-transform: uppercase;
  text-decoration: none;
  background: transparent;
  border: none;
  cursor: pointer;
}
</style>
