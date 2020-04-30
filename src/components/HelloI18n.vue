<template>
  <div>
    <!-- <p>{{ $t('hello', { name }) }}</p>
    <p>{{ $t('goodbye') }}</p>

    <p>{{ $tc('car', 2) }}</p>
    <p>{{ $tc('person', 0) }}</p>
    <p>{{ $tc('person', 1) }}</p>
    <p>{{ $tc('person', 10) }}</p>

    <p>{{ $tc('apple', 0) }}</p>
    <p>{{ $tc('apple', 1) }}</p>
    <p>{{ $tc('apple', 10) }}</p>-->

    <!-- <p>{{ $d(new Date(), "short") }}</p>
    <p>{{ $d(new Date(), "short", 'en-GB') }}</p>
    <p>{{ $d(new Date(), "long") }}</p>-->

    <!-- <p>{{ $n(100, 'currency') }}</p> -->

    <i18n path="terms" tag="p">
      <template slot="termsLink">
        <a href="#">{{ $t('termsLink') }}</a>
      </template>
    </i18n>
    <button @click="setLocale('en')" class="button">English</button>
    <button @click="setLocale('es')" class="button">Spanish</button>
    <button @click="setLocale('de')" class="button">German</button>
  </div>
</template>

<script>
export default {
  name: "HelloI18n",
  data() {
    return {
      name: "Juancho"
    };
  },
  methods: {
    setLocale(locale) {
      this.$i18n.locale = locale;
      localStorage.setItem("locale", locale);
    }
  },
  created() {
    const locale = localStorage.getItem("locale");

    if (locale) {
      this.$i18n.locale = locale;
    } else if (navigator.language) {
      this.$i18n.locale = navigator.language.substring(0, 2);
    }
  }
};
</script>
