<template>
  <body>
    <div class="container">
      <h1>Profile Picture Generator</h1>
    </div>
    <div class="form">
      <form @submit.prevent="submitForm">
        <input type="text" id="input-field" v-model="inputValue" placeholder="Masukkan nama Anda..." required>
        <button type="submit">Buat Profile Picture!</button>
      </form>
      <div v-if="showImage" class="image-wrapper">
        <img :src="imageUrl" alt="Profile Picture">
      </div>
    </div>
  </body>
</template>

<script>
export default {
  data() {
    return {
      inputValue: "",
      showImage: false,
      imageUrl: "",
    };
  },
  methods: {
    submitForm() {
      console.log(this.inputValue);
      this.imageUrl = `https://robohash.org/${this.inputValue}?size=200x200`;
      this.showImage = true;
      this.inputValue = "";
    }
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  margin-top: 20px;
  text-align: center;
}

@media (max-width: 768px) {
  .container {
    max-width: 90%;
    padding: 10px;
  }
}

body {
  justify-content: center;
  align-items: center;
  margin: 0;
  background: lightblue;
}

.form {
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

input[type="text"] {
  margin-bottom: 10px;
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #ccc;
  width: 100%;
  max-width: 300px;
  box-sizing: border-box;
}

button[type="submit"] {
  padding: 10px 25px;
  font-size: 16px;
  border-radius: 5px;
  border: none;
  background-color: green;
  color: #fff;
  cursor: pointer;
}

.image-wrapper {
  align-items: center;
  justify-content: center;
  height: 300px;
  display: flex;
}

img {
  border: 5px solid white;
  border-radius: 25px;
}

</style>
