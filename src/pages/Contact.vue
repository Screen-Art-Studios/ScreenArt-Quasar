<template>
  <div class="main">
    <h2>Contact</h2>
    <div class="contactBox">
      <input class="name" v-model="name" placeholder="Name">
      <input class="email" v-model="email" placeholder="Email">
      <input class="phone" v-model="phone" placeholder="Phone">
      <textarea class="message" v-model="message" placeholder="Send us your message! We understand that your time is important. So we'll do our best to respond quickly!"/>
      <div class="success" v-if="success">Your Message Was Sent!</div>
      <div class="error" v-else-if="error">Oh no! Message Failed. Try Again Later.</div>
      <div v-on:click="send" class="send" v-else>Send</div>
        <h4>(602)-558-1817</h4>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Contact',
  data: function () {
    return {
      success: false,
      error: false,
      name: '',
      email: '',
      phone: '',
      message: '',
      time: {
        month: '',
        day: '',
        hour: '',
        minute: ''
      },
      leadId: ''
    }
  },
  methods: {
    send () {
      let vue = this
      axios.post('https://api.neuronautsolutions.com/deep/contact', {
        name: vue.name.toLowerCase(),
        phone: vue.phone,
        email: vue.email,
        message: vue.message
      })
        .then(function (lead) {
          vue.success = true
        })
        .catch(function (error) {
          console.log(error)
          vue.error = true
        })
    }
  }
}
</script>

<style scoped lang='less'>
  @base-font:'Barlow', sans-serif;

  .main {
    margin-left: 5px;
    margin-right: 5px;
    margin-top: 100px;
    width: 96%;
    height: 68%;
    z-index: 4;
    position: fixed;
    border-radius: 12px;
  }

  h2 {
    font-family: @base-font;
    font-weight: 300;
    font-size: 1.5em;
    color: #008cc4;
    text-align: center;
    line-height: 50px;
    margin: 4px;
  }

  h3 {
    font-family: @base-font;
    font-weight: lighter;
    font-size: 1.2em;
    color: grey;
    text-align: center;
    line-height: 200px;
    grid-column-start: 3;
    grid-column-end: 4;
    margin-right: 20px;
  }

  ul {
    display: grid;
    grid-template-columns: 1fr 1fr;
  }

  h4 {
    width: 100%;
    font-family: @base-font;
    font-weight: lighter;
    font-size: 1.5em;
    color: #008cc4;
    list-style: none;

  }

  .words {
    grid-row: 1;
    grid-column-start: 1;
    grid-column-end: 3;
    font-size: 2em;
    line-height: 0px;
    text-decoration: underline;
  }

  .callus {
    grid-row: 1;
    grid-column-start: 4;
    grid-column-end: 6;
    line-height: 0px;
    font-size: 2.5em;
    text-align: center;
    text-decoration: underline;
    margin-right: 40px;
  }

  .blurb {
    line-height: 27px;
    font-size: 1.3em;
    text-align: center;
    width: 100%;
    margin-top: -15px;
  }

  .contactBox {
    width: 99%;
    text-align: center;
  }

  .success {
    margin-top: 10px;
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row: 6;
  }

  .error {
    margin-top: 10px;
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row: 6;
  }

  .name {
    width: 90%;
    margin-bottom: 5px;
    font-size: 1em;
}

.email {
  width: 90%;
  box-sizing: border-box;
  margin-bottom: 5px;
  font-size: 1em;
}

.phone {
  width: 90%;
  margin-bottom: 5px;
  font-size: 1em;
}

.message {
  width: 90%;
  height: 30vh;
  box-sizing: border-box;
  font-size: 1em;
}

.send {
  width: 90%;
  text-align: center;
  background-color: transparent;
  height: 35px;
  color: #008cc4;
  border: solid 1px #008cc4;
  font-family: @base-font;
  font-size: 1.5em;
  margin-left: 5%;
  margin-top: 4px;
}
.send:hover {
  background-color: #008cc4;
  color: white;
}

#form {
  position: relative;
  width: 500px;
  margin: 50px auto 100px auto;
}

input {
  font-size: 1em;
  font-family: @base-font;
  background: transparent;
  outline: none;
  color: grey;
  border: solid 1px grey;
  height: 4vh;
  transition: all 0.3s ease-in-out;
  -webkit-transition: all 0.3s ease-in-out;
  -moz-transition: all 0.3s ease-in-out;
  -ms-transition: all 0.3s ease-in-out;
}

input:hover {
  background-color: white;
}

textarea {
  width: 90%;
  max-width: 90%;
  height: 110px;
  max-height: 110px;
  padding: 15px;
  background: transparent;
  outline: none;
  color: grey;
  font-family: @base-font;
  font-size: 0.875em;
  border: solid 1px #999;
  transition: all 0.3s ease-in-out;
  -webkit-transition: all 0.3s ease-in-out;
  -moz-transition: all 0.3s ease-in-out;
  -ms-transition: all 0.3s ease-in-out;
}

textarea:hover {
  background-color: white;
}

@media only screen and (min-width:700px) {
  .main {
    margin-left: 10vw;
    margin-top: 25vh;
    width: 80vw;
    height: 100vh;
    z-index: 4;

  }
  h2 {
    font-size: 2em;
  }

}
</style>
