<template>
  <section class="about">
    <input type="text" placeholder="郵便番号を入力" />
    <button>住所自動入力</button>
    <p>Adress:</p>
  </section>
</template>


<script>
import axios from "axios";
export default {
  data() {
    return {
      postcode: "",
      main: "",
      temp: "",
      humidity: "",
      speed: ""
    };
  },
  async created() {
    let item = await axios.get(
      `https://apis.postcode-jp.com/api/v4/postcodes/1000001 \
  -G -v \
  -d "apikey=SpvsoJ8k3yM1wf7KzRf3WogYjKRZlAW2tbOc9e1"

`
    );
    this.data = item.data;
    this.name = this.data.name;
    this.main = this.data.weather[0].main;
    this.temp = this.data.main.temp;
    this.humidity = this.data.main.humidity;
    this.speed = this.data.wind.speed;
  }
};
</script>
