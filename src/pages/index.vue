<template>
  <div class="pb-12">
    <Header />

    <main>
      <div class="container">
        <h1 class="py-8 text-20 text-primary font-bold md:py-10 md:text-26 md:font-medium 2xl:text-34">
          Валютный калькулятор
        </h1>
        <div>
          <p v-if="$fetchState.pending">
            Загружаем котировки...
          </p>
          <p v-else-if="$fetchState.error">
            Не удалось загрузить котировки
          </p>
          <div v-else class="grid gap-8 md:gap-10 xl:gap-12 md:grid-cols-2">
            <form action="">
              <div class="grid grid-cols-1 gap-6">
                <label class="block">
                  <span class="text-14 font-medium text-text-dark">Валюта 1</span>
                  <input v-data="firstCurrencyInput" type="text" class="mt-4 block w-full styled-input" placeholder="Введите название или код">
                </label>
                <label class="block">
                  <span class="text-14 font-medium text-text-dark">Валюта 2</span>
                  <input v-data="secondCurrencyInput" type="text" class="mt-4 block w-full styled-input" placeholder="Введите название или код">
                </label>
                <label class="block">
                  <span class="text-14 font-medium text-text-dark">Количество</span>
                  <input v-data="count" type="text" class="mt-4 block w-full styled-input" placeholder="Введите число">
                </label>
                <div>Итого: ...</div>
              </div>
            </form>
            <div>
              <div class="px-5 py-8 xl:py-12 2xl:px-10 bg-secondary rounded-2xl">
                <h2 class="text-13 font-medium uppercase text-primary xl:text-15 2xl:text-18">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor:
                </h2>
                <div class="grid gap-5 mt-12 md:grid-flow-col md:grid-cols-3 xl:grid-cols-2">
                  <ul class="text-13 styled-list md:col-span-2 xl:text-14 xl:col-span-1 2xl:text-18">
                    <li>Incididunt ut labore et dolore magna aliqua</li>
                    <li>Incididunt ut labore et</li>
                    <li>Incididunt ut labore et dolore</li>
                    <li>Labore et dolore</li>
                    <li>Incididunt ut</li>
                    <li>Incididunt ut labore et dolore</li>
                    <li>Incididunt ut labore</li>
                  </ul>
                  <div class="grid gap-2 grid-cols-4 md:grid-cols-1 md:col-span-1 xl:grid-cols-2">
                    <div
                      class="rounded-tr-[15px] rounded-bl-[15px] bg-image xl:rounded-none"
                      :style="{ backgroundImage: 'url(' + require('~/assets/images/img-1.jpg') + ')' }"
                    />
                    <div
                      class="rounded-tl-[15px] rounded-br-[15px] bg-image xl:rounded-none xl:rounded-tr-[50px]"
                      :style="{ backgroundImage: 'url(' + require('~/assets/images/img-2.jpg') + ')' }"
                    />
                    <div
                      class="rounded-tr-[15px] rounded-bl-[15px] bg-image xl:rounded-none xl:rounded-bl-[50px]"
                      :style="{ backgroundImage: 'url(' + require('~/assets/images/img-3.jpg') + ')' }"
                    />
                    <div
                      class="rounded-tl-[15px] rounded-br-[15px] bg-image xl:rounded-none"
                      :style="{ backgroundImage: 'url(' + require('~/assets/images/img-4.png') + ')' }"
                    />
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="grid gap-7 md:grid-cols-2">
            <div class="text-center md:text-left">
              <strong class="text-16 text-primary">
                Нужна помощь?<br>
                Мы поможем! Просто свяжитесь с нами.
              </strong>
              <p>
                Наши специалисты с радостью ответят на все ваши вопросы и дадут профессиональную консультацию по товарам.
              </p>
            </div>
            <div class="text-center">
              <a href="tel: 88008889028" class="text-26 text-primary">8 (800) 888-90-28</a><br>
              или<br>
              <a href="mailto:info@example.ru" class="text-18 text-primary">info@example.ru</a>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data () {
    return {
      currenciesData: {},
      firstCurrencyInput: '',
      secondCurrencyInput: '',
      firstCurrency: {},
      secondCurrency: {},
      count: null
    }
  },
  async fetch () {
    this.currenciesData = await this.$axios.$get(
      'https://www.cbr-xml-daily.ru/daily_json.js'
    )
  },

  computed: {}
}
</script>

<style lang="scss">
.styled-input {
  padding: 16px 20px;
  border: 1px solid #DFDFDF;
  border-radius: 5px;

  &::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
    color: #A0A3BD;
    opacity: 1; /* Firefox */
  }

  &:-ms-input-placeholder { /* Internet Explorer 10-11 */
    color: #A0A3BD;
  }

  &::-ms-input-placeholder { /* Microsoft Edge */
    color: #A0A3BD;
  }
}

.bg-image {
  background-size: cover;
  padding-bottom: 70%;

  @media (min-width: 1280px) {
    padding-bottom: 100%;
  }
}
</style>
