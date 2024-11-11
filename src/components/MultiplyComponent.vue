<template>
  <div class="MultiplyComponent">
    <!-- After the call I realized I have to capture back the data (My mind was racing too fast),
         so I moved to sending an API request through the script -->
    <form class="MultiplyComponent-form" action="/multiply" method="post"
          @submit.prevent="submitForm">
      <input type="number" v-model="number1">
      <input type="number" v-model="number2">
      <button type="submit">Submit</button>
    </form>
    <div v-show="!!result">
      {{ result }}
    </div>
    <div v-show="!!error">
      {{ error }}
    </div>
  </div>
</template>

<script>
import axios from 'axios';

const BASE_URL = "http://localhost:8000"


export default {
  name: 'MultiplyComponent',
  data() {
    return {
      result: null,
      error: null,
      number1: 0,
      number2: 0,
    }
  },
  methods: {
    submitForm() {
      this.result = null;
      this.error = null;

      const requestData = {
        "number1": this.number1,
        "number2": this.number2,
      }
      
      axios
        .post(BASE_URL + "/multiply", requestData)
        .then((res) => {
          const data = res.data

          if ("result" in data) {
            this.result = data["result"];
          }
          else {
            this.error = "Request has wrong formatting";
          }
        })
        .catch((res) => {
          const data = res.response.data;
          if ("error" in data) {
            this.error = data["error"];
          }
          else {
            this.error = "Response has wrong formatting";
          }
        })
    }
  }
}
</script>