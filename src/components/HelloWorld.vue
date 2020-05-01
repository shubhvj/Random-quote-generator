<template>
  <div id="wrapper">
    <div id="quote-box">
      <h1 id="heading" v-on:click="getQuote">Random Quote Generator</h1>
      <div id="quote-text">{{this.currentQuote}}</div>
      <div id="quote-author">{{this.currentAuthor}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data: function() {
    return {
      quotesData: {},
      parsedJSON: {},
      currentQuote: "",
      currentAuthor: "",
      url:
        "https://gist.githubusercontent.com/camperbot/5a022b72e96c4c9585c32bf6a75f62d9/raw/e3c6895ce42069f0ee7e991229064f167fe8ccdc/quotes.json"
    };
  },
  mounted() {
    this.$axios.get(this.url).then(response => (this.quotesData = response));
    
  },
  methods: {
    parseJSON() {
      console.log(this.quotesData.data.quotes.length);
    },
    getRandomQuote() {
      return this.quotesData.data.quotes[
        Math.floor(Math.random() * this.quotesData.data.quotes.length)
      ];
    },
    getQuote() {
      let randomQuote = this.getRandomQuote();

      this.currentQuote = randomQuote.quote;
      this.currentAuthor = "-" + randomQuote.author;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
body {
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
#wrapper {
  margin: auto;
  width: 50%;
  padding: 120px;
  height: 100%;
}
#quote-box {
  margin: auto;
  width: 50%;
}
#quote-text {
  text-align: center;
  font-size: 20px;
}
#quote-author {
  font-size: 14px;
  text-align: center;
}
.buttons {
  margin-top: 50%;
  text-align: right;
}
#heading {
  text-align: center;
  cursor: pointer;
  background: dimgray;
}
</style>
