<template>
  <header class="bg-gray">
    <nav
      class="h-[50px] flex container items-center"
    >
      <ul class="flex space-x-10">
        <li>
          <NuxtLink
            to="/"
            class="text-12 font-medium text-text-gray-500"
          >
            Калькулятор
          </NuxtLink>
        </li>
        <li>
          <NuxtLink
            to="/currencies"
            class="text-12 font-medium text-text-gray-500"
          >
            Курс рубля
          </NuxtLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  data () {
    return {}
  },

  computed: {}
}
</script>

<style lang="scss">
  nav a.nuxt-link-exact-active {
    color: #343434;
  }
</style>
