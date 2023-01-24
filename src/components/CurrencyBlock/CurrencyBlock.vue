<template>
  <div class="grid gap-5 p-6 xl:py-12 2xl:px-10 bg-gray rounded-2xl currency-block-shadow">
    <div class="h-[50px] w-[50px] xl:h-[56px] xl:w-[56px] 2xl:h-[70px] 2xl:w-[70px]">
      <CurrencyIcon :grow="value > previousValue" />
    </div>
    <div class="text-17 md:text-18 xl:text-20 font-bold text-primary">
      {{ charCode }}
    </div>
    <div class="text-14 xl:text-15 2xl:text-16 text-text-gray-950">
      {{ name }}
    </div>
    <div class="text-14 xl:text-15 2xl:text-16 font-medium text-text-gray-950">
      <ul class="styled-list">
        <li>Номинал: {{ nominal }}</li>
        <li>Курс: {{ value }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import CurrencyIcon from './components/CurrencyIcon.vue'

export default {
  components: { CurrencyIcon },
  props: {
    charCode: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    nominal: {
      type: Number,
      required: true
    },
    value: {
      type: Number,
      required: true
    },
    previousValue: {
      type: Number,
      required: true
    }
  }
}
</script>

<style lang="scss">
ul.styled-list {
  li {
    position: relative;
    padding-left: 1.25em;

    &::before {
      content: '';
      display: block;
      position: absolute;
      top: 50%;
      left: 0;
      height: 0.625em;
      width: 0.625em;
      transform: translateY(-50%);
      border: 2px solid #E02025;
      border-radius: 50%;
    }
  }

  li+li {
    margin-top: .75em;
  }
}

.currency-block-shadow {
  transition: box-shadow .2s;

  &:hover {
    cursor: pointer;
    box-shadow: 0px 2px 10px 0px #00000026;
  }
}
</style>
