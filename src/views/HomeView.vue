<template>
  <div id="home">
    <router-link :to="{name: 'Admin'}">
      <button class="btn">Admin</button>
    </router-link>
    <div id="background-div" class="page-holder">
      <div class="container text-center">
        <h1>Kerekegyensúly</h1>
        <br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>
        <div class="motto">
          <button class="btn-2">Bérles</button>
          <p>Mozgás, Élet, Energia - Kerekegyensúly</p>
        </div>
      </div>
    </div>
    <div class="container-2">
      <div class="wrapper">
        <div class="col-12 text-center">
          <h2 class="pt-3">Kategóriáink</h2>
        </div>
      </div>
      <div class="wrapper">
        <div v-for="index in this.categorySize" :key="index" class="col-md-4 col-xl-3 col-6 pt3 justify-content-around d-flex">
          <CategoryBox :category="categories[index-1]"></CategoryBox>
        </div>
      </div>
    </div>
    <div class="container-3">
      <div class="wrapper">
        <div class="col-12 text-center">
          <h2 class="pt-3">Termékeink</h2>
        </div>
      </div>
      <div class="wrapper">
        <div v-for="index in this.productSize" :key="index" class="col-md-4 col-xl-3 col-6 pt3 justify-content-around d-flex">
          <ProductBox :product="products[index-1]"></ProductBox>
        </div>
      </div>
    </div>
    <div class="container-4">
      <div class="wrapper">
        <div class="col-12 text-center">
          <h2 class="pt-3">Rólunk</h2>
        </div>
      </div>
      <div class="wrapper" id="#rolunk">
        <div class="aboutus">
          <h4 class="text-center">Üdvözlünk, mi a Kerekegyensúly bicikli és elektromos roller kölcsönző vagyunk</h4>
          <h3>Célunk:</h3>
          <p>
            A Szeged város zöldebbé tétele, azzal hogy kibérelik elekromos rollereinket ahelyett, hogy járművükkel járnának az emberek a mindennapjaikban.
            A családok és egyéb társaságok számára a szabadság élményét átadni.
            A zöld élet népszerűsítése.
            Mottónk a Mozgás, Élet, Energia.
            Mozgás fontossága, az élet kiegyensúlyozása és a megújuló és tiszta energia használata.
          </p>
          <h3>Előnyeink:</h3>
          <ul>
            <li>A túrázok minden túra előtt tetszés szerint tudnak választani túravezetőink közül.</li>
            <li>Ha probléma akad a bicikli vagy az elektromos rollerrel kapcsolatban, akkor tudunk segíteni.</li>
            <li>Turisták számára a cégünk kínál e-térképet rajta a látványosságokkal illetve népszerű útvonalainkal.</li>
            <li>A vásárlóink a lehető legjobb és legmodernebb bicikli és ellektromos roller kínálatból válaszhatnak.</li>
            <li>Mindezek mellett a túrázóknak van lehetőség többféle túraútvonal kiválasztására is, a hangulatos rövid családi kirándulás vagy akár a több napig is tartó túrák, nálunk mindent megtalál.</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CategoryBox from "../components/category/CategoryBox";
import ProductBox from "../components/ProductBox";
export default {
  name: "HomeView",
  components: {ProductBox, CategoryBox},
  props: ["categories", "products"],
  data() {
    return {
      categorySize: 0,
      productSize: 0
    }
  },
  mounted() {
    this.categorySize = Math.min(6, this.categories.length );
    this.productSize = Math.min(8, this.products.length);
  }
};
</script>
<style scoped>
.aboutus {
  margin: 20px;
  padding-left: 30px;
  padding-right: 30px;
}
.aboutus p {
  text-align: start;
}
h1 {
  font-family: "Barlow"; 
  font-weight: 600;
  font-size:42px;
}
.btn{
  position: relative;
  margin-top: 20px;
  width: 310px;
  height: 50px;
  border: none;
  outline: none;
  background: rgb(240, 239, 239);
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  font-size: 16px;
  font-weight: 600;
  color:black;
}
p {
  text-align: center;
  margin-top: 10px;
  background-color: transparent;
}
.container {
  padding-top: 100px;
}
.container-2 {
  margin-top: 20px;
}
.container-3 {
  margin-top: 30px;
  margin-bottom: 15px;
}
.btn-2{
  position: relative;
  margin-top: 0px;
  width: 150px;
  height: 40px;
  border: none;
  outline: none;
  background: transparent;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  font-weight: 600;
  color:black;
}
.btn-2:hover{
  transition: all 0.1s ease-in-out;
  transform: scale(1.03);
  background: transparent;
  border-radius: 5px;
  border: solid 1px black;
  cursor: pointer;
  color:black;
}
.page-holder {
  min-height: 100vh;
}
#background-div {
  background: url("../assets/bikebg.png");
  background-size: cover !important;
  background-repeat: no-repeat;
  background-position: center;
}
</style>


