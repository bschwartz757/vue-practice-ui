<template>
  <div class="card">
    <figure class="card__image">
      <img :src="productImage" alt />
    </figure>
    <div class="card__item">
      <p
        class="card__details-text--bold"
      >Apply for the REI Co-op Mastercard and you could be instantly approved and earn a $100 REI gift card</p>
      <p>
        Upon approval, you'll also get 5% back on this purchase. Plus, you'll get 1% back everywhere else you use your card.
        <a
          href="#"
        >Learn more & apply now</a>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CreditCard",

  data() {
    return {
      image: "mastercard.png"
    };
  },
  computed: {
    /*
    Provides the image path for the product image
    */
    productImage() {
      return require(`@/assets/${this.image}`);
    }
  },
  methods: {}
};
</script>

<style lang="scss" scoped>
@import "../styles/CreditCard.scss";
</style>
