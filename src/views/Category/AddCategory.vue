<template>
    <body>
        <div class="container">
        <div class="wrapper">
            <div class="col-12 text-center"><h2>Kategória hozzáadása</h2></div>
            <form class="addcat">
                <div class="input-box">
                    <label for="name">Kategória</label>
                    <input type="text" class="name" placeholder="Kategória neve" v-model="categoryName" required>
                </div>
                <div class="input-area">
                    <label for="desc">Leírás</label>
                    <textarea type="text" class="desc" placeholder="Kategória leírása" v-model="description" required></textarea>
                </div>
                <div class="input-box">
                    <label for="img">Kép</label>
                    <input type="url" class="img" placeholder="Kategória képe" v-model="imageUrl" required>
                </div>
                <button type="button" class="btn" @click="addCartegory">KÉSZ</button>
            </form>
        </div>
    </div>
    </body>
    
</template>
<script>
const axios = require("axios");
const sweetalert = require("sweetalert");
export default {
  data() {
    return {
      categoryName: "",
      description: "",
      imageUrl: "",
    };
  },
  methods: {
    addCategory() {
      console.log(this.categoryName, this.description);
      const newCategory = {
        categoryName: this.categoryName,
        description: this.description,
        imageUrl: this.imageUrl,
      };

      const baseURL = "https://limitless-lake-55070.herokuapp.com";

      axios({
        method: "post",
        url: `${baseURL}/category/create`,
        data: JSON.stringify(newCategory),
        headers: {
          "Content-Type": "application/json",
        },
      })
        .then(() => {
          sweetalert({
            text: "Category added successfully",
            icon: "success",
          });
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
<style scoped>
body {
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
    
}

.wrapper {
    width: 420px;
    background-color: transparent;
    backdrop-filter: blur(20px);
    border: 2px solid rgba(255, 255, 255, 0.2);
    box-shadow: 0 0 10px rgba(0 0 0 0.1);
    color: rgba(0, 0, 0, 1);
    padding: 30px 40px;
    border-radius: 10px;
}

.wrapper .input-box {
    position: relative;
    width: 100%;
    height: 30px;
    margin: 50px 0;
}

.wrapper .input-area {
    position: relative;
    width: 100%;
    height: 30px;
    margin-bottom: 70px;
}

.input-box input{
    width: 100%;
    height: 100%;
    border: none;
    outline: none;
    border-radius: 40px;
    font-size: 16px;
    color: rgba(0, 0, 0, 1);
    padding: 20px 45px 20px 20px;
}
.input-area textarea{
    width: 100%;
    height: 200%;
    border: none;
    outline: none;
    border-radius: 5px;
    font-size: 16px;
    color: rgba(0, 0, 0, 1);
    padding: 20px 45px 20px 20px;
}
.input-box input::placeholder, .input-area input::placeholder{
    color: rgba(0, 0, 0, 0.5);
}

.wrapper .btn {
    margin-top: 20px;
    width: 100%;
    height: 50px;
    border: none;
    outline: none;
    background: #fff;
    border-radius: 40px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    font-size: 16px;
    font-weight: 600;
    color:black;
}

.wrapper .btn:hover {
    margin-top: 20px;
    width: 100%;
    height: 50px;
    border: none;
    outline: none;
    background:rgb(240, 239, 239);
    transition: all 0.15s ease;
    transform: scale(1.02);
    border-radius: 40px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    font-size: 16px;
    font-weight: 600;
    color:black;
}

h2{
    font-size: 28px;
}
</style>
