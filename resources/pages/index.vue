<template>
  <div class="container">
    <!--Layout-->
        <div class="front">
          <header><img src="@/assets/img/banner.png"/></header>
           <div id="playSpace">
             <!-- attempt to figure out GET requests
              <form>
                  <h1>Player Numbers</h1>
                  <h2>Player 1 number</h2>
                  <input type="text" v-model.number="guess.num1" required>
                  <h2>Player 2 number</h2>
                  <input type="text" v-model.number="guess.num2" required>
                  <h2>Player 3 number</h2>
                  <input type="text" v-model.number="guess.num3" required/>
              </form>
              <div id="preview">
                  <h1>Output</h1>
                  <p>p1:{{guess.num1}}</p>
                  <p>p2:{{guess.num2}}</p>
                  <p>p3:{{guess.num3}}</p>
              </div>
              <button class="button" v-on:click.prevent="post">Send</button>
            </div>
            -->
          <div id="playSpace">
            <p>{{randNum()}}</p>
                <div class="p1">
                <!--vue number adder for each player-->
                <p>Enter a number </br> between 0 and 100</p>
                <input v-model="guess.num1" id="min" min="0" max="100" type="number"></br>
                <button class="button" @click.prevent="p1Sent">Submit</button>
              </div>
              <div class="p2">
                <p>Enter a number </br> between 0 and 100</p>
                <input v-model="guess.num2" id="min" min="0" max="100" type="number"></br>
                <button class="button" @click="p2Sent">Submit</button>
              </div>
              <div class="p3">
                <p>Enter a number </br> between 0 and 100</p>
                <input v-model="guess.num3" id="min" min="0" max="100" type="number"></br>
                <button class="button" @click="p3Sent">Submit</button>
                </div>
              </div>
          </div>
        </div>
  </div>
</template>

<script>
export default {
   data(){
     return{
        guess:{
          num1:"",
          num2:"",
          num3:""
        }
      }
   },
  methods:{
    post:function(){
      this.$http.post('https://jsonplaceholder.typicode.com/posts',{
        userId: this.guess.num1
      }).then(function(data){
        console.log();
      });
    },
     randNum : function(){
       return Math.floor(Math.random() * 100);
     }
  },

}

</script>

<style>
.container {
  display: flex;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

body{
  position: relative;
  height: auto;
  min-height: 100% !important;
  padding: 1.5em;
}

img{
  object-fit: fill;
  width: 100%;
  height: 10em;
}


.front{
  height: 100%;
  margin: 12px;
  border: 1px solid gray;
  padding: 3em;
  border-radius: 4px;
}

#playSpace{
  text-align: center;
}

#min{
  text-align: center;
  font-size: 16px;
  border-radius: 3px;
  height: 2em;
  width: 6.5em;
}

.p1, .p2, .p3{
  text-align: center;
  font: 16px arial, sans-serif;
  border: 1px solid gray;
  border-radius: 2px;
  padding: 4em;
  width: 32%;
  height: 21em;
  display: inline-block;
}

.p1{
  float: left;
}

.p2{
  float: right;
}

p{
  margin-top:2em;
}

button:hover {
  transition: background-color 0.35s ease-in;
    background-color: #00cc00;
}

button{
    font-size: 14px;
    border:1px solid black;
    box-shadow: 0.5px .7px .6px #888888;
    font-weight: bold;
    position: relative;
    display: inline-block;
    border-radius: 2px;
    color: #fff !important;
    text-decoration: none;
    padding: 0.65em .5em 0.65em .5em;
    background-color: #00a800;
    cursor: pointer;
    margin-top:10px;
}

/* Small devices (tiny phones, 320px and up) */
@media only screen and (min-width: 320px) {
body{
    padding: .7766em;
}

img{
  height: 5em;
}

.p1, .p2, .p3{
  text-align: center;
  font: 16px arial, sans-serif;
  border: 1px solid gray;
  border-radius: 2px;
  padding: .5em;
  width: 100%;
  height: 12em;
  display: inline-block;
  margin-top: 20px;
}

#min{
  font-size: 14px;
  border-radius: 3px;
  height: 2em;
  width: 6em;
}

button{
  font-size: 14px;
}


}

/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (min-width: 768px) {
body{
    padding: .7766em;
}

img{
  height: 12em;
}

.p1, .p2, .p3{
  text-align: center;
  font: 18px arial, sans-serif;
  border: 1px solid gray;
  border-radius: 2px;
  padding: .5em;
  width: 100%;
  height: 14em;
  display: inline-block;
  margin-top: 20px;
}

#min{
  font-size: 18px;
  border-radius: 3px;
  height: 2em;
  width: 6em;
}

button{
  font-size: 18px;
}
}

/* Large devices (laptops/desktops, 992px and up) */
@media only screen and (min-width: 992px) {
body{
    padding: .5em;
}

img{
  object-fit: fill;
  width: 100%;
  height: 12em;
}

.p1, .p2, .p3{
  font: 24px arial, sans-serif;
  width: 32%;
  height: 14em;
}

#min{
  font-size: 24px;
  border-radius: 3px;
  height: 2em;
  width: 6em;
}

button{
    font-size: 24px;
}
}

/* Extra large devices (large laptops and desktops, 1200px and up) */
@media only screen and (min-width: 1200px) {
body{
    padding: .7766em;
}

img{
  height: 10em;
}

.p1, .p2, .p3{
  font: 18px arial, sans-serif;
  padding: 3em;
  width: 32%;
  height: 18em;
}

#min{
  font-size: 18px;
  border-radius: 3px;
  height: 2em;
  width: 6em;
}

button{
  font-size: 18px;
}

}

/*Extra Large Devices big screens 1900px and up*/
@media screen and (min-width: 1900px) {
body{
    width:100%;
}

img{
  height: 30em;
}

.front{
  width:100%;
}
.p1, .p2, .p3{
  font: 60px arial, sans-serif;
  padding: .5em;
  width: 32%;
  height: 14em;
}

#min{
  font-size: 60px;
  border-radius: 3px;
  height: 2em;
  width: 6em;
}

button{
  font-size: 60px;
  margin-top:1em;
}

}

</style>
