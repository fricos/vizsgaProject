<template>
    <div class="container">
        <div class="wrapper pt-5">
            <div class="col-md-1"></div>
            <div class="col-md-4 col-12">
                <img src="product.imageURL" alt="" class="img-fluid">
            </div>
            <div class="col-md-6 col-12 pt-3 pt-md-0">
                <h4>{{ product.name }}</h4>
                <h6>{{ category.categoryName }}</h6>
                <h6 class="font-weight-bold">{{ product.price }} ft</h6>
                <p>{{ product.description }}</p>

                <div class="d-flex flex-row justify-content-between">
                    <div class="input-group col-md-3 col-4 p-0">
                        <div class="input-group-pretend">
                            <span class="input-group-text">
                                darab
                            </span>
                        </div>
                        <input type="number" class="form-control" v-model="quantity"/>
                    </div>
                    <div class="input-group col-md-3 col-4 p-0">
                        <button class="btn">Hozzáadás a kosárba</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import swal from "sweetalert";
import axios from "axios";
export default {
  data() {
    return {
      product: {},
      category: {},
      quantity: 1,
      wishListString: "Add to wishlist",
    };
  },
  props: ["baseURL", "products", "categories"],
  methods: {
    addToWishlist() {
      if (!this.token) {
        // user is not logged in
        // show some error
        swal({
          text: "please login to add item in wishlist",
          icon: "error",
        });
        return;
      }
      // add item to wishlist
      axios
        .post(`${this.baseURL}wishlist/add?token=${this.token}`, {
          id: this.product.id,
        })
        .then((res) => {
          if (res.status === 201) {
            this.wishListString = "Added to Wishlist";
            swal({
              text: "Added to Wishlist",
              icon: "success",
            });
          }
        })
        .catch((err) => {
          console.log("err", err);
        });
    },

    // add to cart

    addToCart() {
      if (!this.token) {
        // user is not logged in
        // show some error
        swal({
          text: "please login to add item in cart",
          icon: "error",
        });
        return;
      }

      // add to cart

      axios
        .post(`${this.baseURL}/cart/add?token=${this.token}`, {
          productId: this.id,
          quantity: this.quantity,
        })
        .then((res) => {
          if (res.status == 201) {
            swal({
              text: "Product added in cart",
              icon: "success",
            });
          }
        })
        .catch((err) => console.log("err", err));
    },
  },
  mounted() {
    this.id = this.$route.params.id;
    this.product = this.products.find((product) => product.id == this.id);
    this.category = this.categories.find(
      (category) => category.id == this.product.categoryId
    );
    this.token = localStorage.getItem("token");
  },
};
</script>
<style scoped>
.btn {
    background-color: #b9b9b9;
}
.category {
  font-weight: 400;
}
</style>