<template>
  <div>
    <input
      type="text"
      placeholder="Search Product.."
      v-model="search"
    />
    <ul class="listOfProducts">
      <li v-for="(product, index) in filteredList" :key="index" class="product">
        <img :src="product.img" alt="" width="250px" height="250px"/>
        <router-link to="/product-details">
          <h2 class="product-name" @click="addCurrentProduct(product)">
            {{ product.Title | truncate(25) }}
          </h2>
        </router-link>
        <div class="product-price">
          <span>${{ product.price }}, 00</span>
          <span>10 x ${{ Math.round(product.price / 10) }}, 00 </span>
        </div>

        <btn
          btnColor="btn btn-large btn-sucess"
          :cartIcon="true"
          @click.native="addProductToCart(product)"
        >
          Add to cart
        </btn>
      </li>
    </ul>
  </div>
</template>

<script>
import { mapActions } from "vuex";
import btn from "./Btn";
import Menu from "./Menu.vue";

export default {
  props: ["products"],

  data(){
    return {
      search: ""
    }
  },

  computed: {
    filteredList: function(){
      return this.products.filter((product) => {
        return product.Title.toLowerCase().match(this.search.toLowerCase())
      })
    }
  },

  components: {
    btn,
    Menu,
  },
  methods: {
    ...mapActions(["addProduct", "currentProduct", "filteredList"]),

    addProductToCart(product) {
      this.addProduct(product);
    },
    addCurrentProduct(product) {
      this.currentProduct(product);
    },
  },
};
</script>

<style scoped>
.listOfProducts {
  width: 100%;
  max-width: 1000px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  padding: 50px;
}

.product {
  width: 300px;
  background-color: #fff;
  list-style: none;
  box-sizing: border-box;
  padding: 1em;
  margin: 1em 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 7px;
}

.product:hover {
  background-color: rgb(172, 233, 160);
}
input {
  width: 295px;
  background-color: #fff;
  padding: 1em;
  margin: 1em;
  position: absolute;
  display: flex;
  align-items: center;
  border-radius: 7px;
  left: 41%;
  top: -7px;
}

.product-name {
  font-size: 1.2em;
  font-weight: normal;
}

.product-name:hover {
  cursor: pointer;
  text-decoration: underline;
}

.product-price {
  width: 100%;
  align-self: flex-start;
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5em;
}
</style>

