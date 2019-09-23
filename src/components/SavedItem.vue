<template>
  <div class="item">
    <div class="item__details">
      <figure class="item__details__image">
        <img :src="productImage" alt />
      </figure>
      <div class="item__details__item">
        <a href="#" class="item__details__name">
          <span class="item__details__brand">{{ item.brand }}</span>
          {{item.name}}
        </a>
        <span class="item__details__color">{{ item.color }}</span>
        <span class="item__details__size">{{ item.size }}</span>
        <span class="item__details__sku">#{{ item.sku }}</span>

        <div class="item__details__buttons">
          <button
            :id="`save-for-later-btn-${item.sku}`"
            type="button"
            name
            @click="moveToCurrentItems"
            class="btn btn--small"
          >Move to cart</button>
          <button
            :id="`remove-btn-${item.sku}`"
            type="button"
            name
            @click="removeItemFromSaved"
            class="btn btn--small"
          >Remove</button>
        </div>
      </div>
    </div>
    <div class="item__options">
      <div class="item__options__inner">
        <div class="item__options__row item__options__row--pricing">
          <div class="item__options__price">
            <span>${{ formattedPrice }}</span>
          </div>
          <div class="item__options__total">
            <span>{{ totalPrice }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SavedItem",

  props: {
    item: {
      type: Object,
      default: () => {}
    }
  },
  computed: {
    /*
    Provides the image path for the product image
    */
    productImage() {
      // return import `@/assets/${this.item.img}`;
      return require(`@/assets/${this.item.img}`);
    },

    /* Formats the price number so it's padded with zeroes
     */
    formattedPrice() {
      return this.item.price.toFixed(2);
    },

    /* Calculates the total price of the product */
    totalPrice() {
      const total = this.item.price * this.item.quantity;
      return total.toFixed(2);
    }
  },
  methods: {
    moveToCurrentItems() {
      this.$emit("move-to-cart", this.item.id);
    },
    removeItemFromSaved() {
      this.$emit("remove", this.item.id);
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../styles/CartItem.scss";
</style>
