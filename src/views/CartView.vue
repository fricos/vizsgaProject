<template>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h3 class="pt-3">
            Bevásárló kocsi
          </h3>
        </div>
      </div>
      <div v-for="cartItem in cartItems" :key="cartItem.id" class="row mt-2 pt-3">
        <div class="col-2"></div>
        <div class="col-md-3">
          <img
            :src="cartItem.product.imageURL"
            alt=""
            class="w-100 card-image-top embed-responsive embed-responsive-16by9"
            style="object-fit: cover"
          />
        </div>
        <div class="col-md-5 px-3">
          <div class="card-block px-3">
            <h6 class="card-title">
              {{ cartItem.product.name }}
            </h6>
  
            <p class="mb-0 font-weight-bold" id="item-price">
              Ft {{ cartItem.product.price }} per darab
            </p>
            <p class="mb-0">Mennyiség:{{ cartItem.quantity }}</p>
          </div>
          <p class="mb-0">
            Összesen:
            <span class="font-weight-bold">
              Ft {{ cartItem.product.price * cartItem.quantity }}
            </span>
          </p>
        </div>
        <div class="col-2"></div>
        <div class="col-12"><hr /></div>
      </div>
      <div class="total-cost pt-2 text-right">
        <h5>Összesen : Ft{{ totalCost }}</h5>
      </div>
    </div>
  </template>
  <script>
  import axios from "axios";
  export default {
    data() {
      return {
        cartItems: [],
        token: null,
        totalCost: 0,
      };
    },
    props: ["baseURL"],
    methods: {
      listCartItems() {
        axios
          .get(`${this.baseURL}cart/?token=${this.token}`)
          .then((res) => {
            const result = res.data;
            this.cartItems = result.cartItems;
            this.totalCost = result.totalCost;
          })
          .catch((err) => console.log("err", err));
      },
    },
    mounted() {
      this.token = localStorage.getItem("token");
      this.listCartItems();
    },
  };
  </script>