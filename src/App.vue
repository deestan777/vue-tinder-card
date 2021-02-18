<template>
  <div id="app">
    <div v-if="visibleCards == 0" id="result">
      <div id="percentStat">
        <p>
          <img
            svg-inline
            class="icon"
            src="./assets/icon_happy.svg"
            alt="happy"
          />
          {{ swipeAccept * (visibleCards.length + 1) * 20 }}%
     
          <img svg-inline class="icon" src="./assets/icon_sad.svg" alt="sad" />
          {{ swipeRejected * (visibleCards.length + 1) * 20 }}%
        </p>
        <p>
          <img
            svg-inline
            class="icon"
            src="./assets/icon_heart.svg"
            alt="hearth"
          />
          {{ swipeSkipped * (visibleCards.length + 1) * 20 }}%
        </p>
      </div>
    </div>
    <div v-else id="nav">
      <div>
        <button class="radial">
          <i>
            <img svg-inline class="icon" src="./assets/Union.svg" alt="happy" />
          </i>
        </button>
        <button class="radial">
          <i>
            <img
              svg-inline
              class="icon"
              src="./assets/btn_retry.svg"
              alt="happy"
            />
          </i>
        </button>
      </div>
      <div id="center">
        <h2>Параметры:</h2>
        <div id="clickStat" v-if="visibleCards.length == 0">

/* sad icon */

          <p>
            <img
              svg-inline
              class="icon"
              src="./assets/icon_sad.svg"
              alt="sad"
            />
            {{ swipeRejected * (visibleCards.length + 1) * 20 }}%
          </p>

/* happy icon */

          <p>
            <img
              svg-inline
              class="icon"
              src="./assets/icon_happy.svg"
              alt="happy"
            />
            {{ swipeAccept * (visibleCards.length + 1) * 20 }}%
          </p>

/* heart icon */

          <p>
            <img
              svg-inline
              class="icon"
              src="./assets/icon_heart.svg"
              alt="hearth"
            />
            {{ swipeSkipped * (visibleCards.length + 1) * 20 }}%
          </p>
        </div>

        <div id="clickStat" v-else>
          <p>
            <img
              svg-inline
              class="icon"
              src="./assets/icon_sad.svg"
              alt="sad"
            />
            {{ swipeRejected }}
          </p>
          <p>
            <img
              svg-inline
              class="icon"
              src="./assets/icon_happy.svg"
              alt="happy"
            />
            {{ swipeAccept }}
          </p>
          <p>
            <img
              svg-inline
              class="icon"
              src="./assets/icon_heart.svg"
              alt="hearth"
            />
            {{ swipeSkipped }}
          </p>
        </div>
      </div>
      <div id="clients">
        <div>
          <p>Осталось в очереди</p>
          <p>
            <span id="countClients">{{ visibleCards.length }}</span
            >/5
          </p>
        </div>
      </div>
    </div>
    <GameCardStack
      :cards="visibleCards"
      @cardAccepted="handleCardAccepted"
      @cardRejected="handleCardRejected"
      @cardSkipped="handleCardSkipped"
      @hideCard="removeCardFromDeck"
    />
  </div>
</template>

<script>
import GameCardStack from "./components/GameCardStack";

export default {
  name: "App",
  components: {
    GameCardStack
  },

  data() {
    return {
      visibleCards: [
        /*
        "Марія, 19 років",

        "Степан, 61 рік",

        "Любов, 58 років",

        "Олександр, 20 років",

        "Ірина, 55 років"
        */
      {class: 'Марія, 19 років',  src: '1-Smart 2.jpg', text : 'Бабуся приймає брендовий препарат від болю в суглобах, він допомагає, але занадто дорогий. У Вас є якісний аналог з нижчою ціною? Якщо ні — давайте бренд.'},
      {class: 'Степан, 61 рік', src: '8-Poor 2.jpg',  text : 'Спросоння відсунув гарячий чайник рукою та обпікся. У Вас всі ліки від опіків такі дорогі? Можна хороший препарат недорого?'},
      {class: 'Любов, 58 років', src: '3-Smart 1.jpg',  text : 'Лікар призначив препарат від артеріальної гіпертензії, а бренд дорого коштує. Тому мені потрібен аналог з хорошою ефективністю та приємною ціною.'},
      {class: 'Олександр, 20 років', src: '4-Smart 1.jpg',  text : 'Порекомендуйте ефективний препарат від болю в горлі за розумну ціну.'},
      {class: 'Ірина, 55 років', src: '5-Smart 1.jpg',  text : 'У мене часто невралгії, лікар призначив вітаміни групи В. Мені потрібен якісний аналог за прийнятною ціною.'},
      ],
      swipeAccept: 0,
      swipeRejected: 0,
      swipeSkipped: 0
    };
  },
  methods: {
    handleCardAccepted() {
      console.log("handleCardAccepted");
      this.swipeAccept += 1;
    },
    handleCardRejected() {
      console.log("handleCardRejected");
      this.swipeRejected += 1;
    },
    handleCardSkipped() {
      console.log("handleCardSkipped");
      this.swipeSkipped += 1;
    },
    removeCardFromDeck() {
      this.visibleCards.shift();
    }
  }
};
</script>

<style lang="scss">
@import "./styles/mixins.scss";
#app {
  width: 100vw;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  text-align: center;
}
#nav {
  position: fixed;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-image: url("./assets/pink_bg.png");
  width: 35%;
  height: 100vh;
  h2 {
    text-align: left;
    color: white;
  }
  div:nth-child(3) {
    background: #fff5;
    color: white;
    height: 134px;

    p {
      font-weight: 400 !important;
      letter-spacing: 1px;
      font-size: 40px;
      line-height: 60px;
      font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS",
        sans-serif;
      text-shadow: 5px 0 12px black;
    }
  }
  div:nth-child(2){
    position: relative;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    #clickStat{

        p {
          font-size: 45px;
          font-weight:400;
          color:#424242;
          line-height: 70px;
          width: 45%;
          margin: 10px;
          padding: 15px;
          text-align: center;
          background: #fff;
          border-radius: 50px;
          
        }
        img{
          transform: translate(-40px,10px);
        }
        
    }
  }
  #percentStat{
    display: flex;
    flex-direction: row;
  }
  #clickStat{
    p{
    width: 45%;
    }
  }
  #countClients {
    font-weight: bolder;
    font-size: 45px;
    color: white;
  }

#clients {
  width: 100%;
  display: flex;
  flex-direction: column;
}
.radial {
  width: 70px;
  height: 70px;
  margin: 10px;
  border-radius: 50%;
  background: rgb(255, 255, 255);
}
}
</style>