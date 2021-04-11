<template>
  <div class="container">
    <form @submit.prevent="sendEmail">
      <label>Name</label>
      <input type="text" v-model="name" name="name" placeholder="Your Name" />
      <label>Email</label>
      <input
        type="email"
        v-model="email"
        name="email"
        placeholder="Your Email"
      />
      <label>Message</label>
      <textarea
        name="message"
        v-model="message"
        cols="30"
        rows="5"
        placeholder="Message"
      >
      </textarea>

      <button type="submit">Enviar</button>
    </form>
  </div>
</template>
<script>
import emailjs from "emailjs-com";

export default {
  data: () => ({
    name: "",
    message: "",
    email: ""
  }),
  methods: {
    sendEmail: function(e) {
      try {
        console.log(process.env.VUE_APP_USER_ID);
        emailjs.sendForm(
          process.env.VUE_APP_SERVICE_ID,
          process.env.VUE_APP_TEMPLATE_ID,
          e.target,
          process.env.VUE_APP_USER_ID,
          {
            name: this.name,
            email: this.email,
            message: this.message
          }
        );
      } catch (err) {
        console.log({ err });
      }

      this.name = "";
      this.email = "";
      this.message = "";
    }
  }
};
</script>
<style scoped>
* {
  box-sizing: border-box;
}

.container {
  display: block;
  margin: auto;
  text-align: center;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  width: 50%;
}

label {
  float: left;
}

input[type="text"],
[type="email"],
textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

button {
  background-color: #4caf50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>
