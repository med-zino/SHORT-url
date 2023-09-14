<template>
  <form action="">
    
    <input type="text" v-if="!done" placeholder="Enter the long URL here" v-model="longUrl" >
    <input type="text" v-if="done" placeholder="Enter the long URL here" v-model="shortUrl" disabled >
    <button v-if="!done" @click.prevent @click="shortenUrl">Generate the shorter link</button>
    <button v-if="done" @click.prevent @click="copyToClipboard" >Copy</button>
    <button v-if="done" @click.prevent @click="refresh" >Again ?</button>

     <span class="copy-message" v-if="copySuccess">Copied!</span>

  </form>
</template>

<script>
import axios from 'axios';
export default {

data(){
return {
longUrl : "",
shortUrl: "",
done: false,
copySuccess:false
} 
},

methods : {

 

    async shortenUrl () {
    const encodedParams = new URLSearchParams();
    encodedParams.set('url', this.longUrl);
    const options = {
        method: 'POST',
        url: 'https://url-shortener-service.p.rapidapi.com/shorten',
        headers: {
          'content-type': 'application/x-www-form-urlencoded',
          'X-RapidAPI-Key': '0db77bb548msh9ea6798adb4cbd1p174554jsn3f0e3af19743',
          'X-RapidAPI-Host': 'url-shortener-service.p.rapidapi.com'
        },
        data: encodedParams,
      };
       try {
        const response = await axios.request(options);
        this.shortUrl = response.data.result_url
        this.done = true
      } catch (error) {
        console.error(error);
      }
    },

     copyToClipboard() {
      const inputElement = document.createElement("input");
      inputElement.value = this.shortUrl;
      document.body.appendChild(inputElement);
      inputElement.select();
      document.execCommand("copy");
      document.body.removeChild(inputElement);
      this.copySuccess = true
      // You can also provide feedback to the user that the text has been copied, e.g., using a tooltip or a message.
    },

    refresh(){
        location.reload()
    }
}

}
</script>

<style>

form {
    width: 320px;
    color: white;
    margin: 360px auto 0 auto;
    border-radius: 7px;
    overflow: hidden;
    border: 1px solid #30363d;


}

label {
    display: inline-block
}

input {
    display: block;
    margin: 0;
    width: 300px;
    height: 40px;
    border: none;
    padding: 0 12px;
    outline: none;
}

button {
    margin: 0;
    width: 325px;
    height: 40px;
    border: none;
    background: #0d1117;
    color: #d9d9d9;
    padding: 0 12px;
    outline: none;  
    text-align: left;
}

input:focus {
    border: none;
     box-shadow: 0 0 10px rgba(255, 255, 255, 0.6);
}

input:disabled {
    background-color: white;
}

.copy-message {
  color: white; /* Change the color as needed */
  font-size: 14px; /* Adjust the font size as needed */
  margin-left: 10px; /* Add spacing from the button */
}

</style>