<template>
    <body>
        <div class="container">
            <div class="blur">
                <div class="row">
                <div class="col-12 text-center">
                    <h2>Kategóriáink</h2>
                    <router-link :to="{name: 'AddCategory'}">
                        <button class="btn">Kategória hozzáadása</button>
                    </router-link>
                </div>
            </div>
            <div class="row">
                <div v-for="category of categories" 
                :key="category.id" 
                class="col-xl-4 col-md-6 col-12 pt-3 d-flex"
                >
                    <CategoryBox :category="category"></CategoryBox>
                </div>
            </div>
            </div>
        </div>
    </body>
</template>
<script>

import CategoryBox from '@/components/category/CategoryBox.vue';
export default {
  name: "CategoryView",
  props:["categories"],
  components: { CategoryBox },
  data() {
    return {
      baseURL: "https://limitless-lake-55070.herokuapp.com",
    };
  },
  methods: {
  },
  mounted() {},
};
</script>
<style scoped>
body{
    background: url(https://cdn.discordapp.com/attachments/1153584270158331975/1168999891318612060/szines_bicikli_illusztracio.jpg?ex=65cbc77d&is=65b9527d&hm=6c5765dcc5ea4404387493fae95a74a2fbbc91098c6d628a4b17f8d2af37be13&);
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
}
.container{
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    width: 100%;
}

.blur{
    width: 100%;
    background-color: transparent;
    backdrop-filter: blur(20px);
    border: 2px solid rgba(255, 255, 255, 0.2);
    box-shadow: 0 0 10px rgba(0 0 0 0.1);
    color: rgba(0, 0, 0, 1);
    padding: 30px 40px;
    border-radius: 10px;
}

.btn {
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


</style>
