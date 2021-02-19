<template>
  <div id="app">
    <div id="start">
      <div id="circle">
        <p>Добро пожаловать в игру</p>
        <p>
          Помоги <br />
          ФАРМАЦЕВТУ
        </p>
        <a onclick="document.getElementById('start').remove()">Начать</a>
      </div>
    </div>

    <div v-if="visibleCards == 0" id="result">
      <div id="end">
        <div id="percentStat">
          <p id="percents">

            {{ swipeRejected * (visibleCards.length + 1) * 20 }}%


            {{ swipeAccept * (visibleCards.length + 1) * 20 }}%


            {{ swipeSkipped * (visibleCards.length + 1) * 20 }}%
          </p>
          <p id="drug">Препарат 1 Препарат 2 Препарат 3</p>

          <hr />
          <p id="wtf">
            Ваш результат: <br />
            «Что я здесь делаю?»
          </p>
          <p id="thistest">
            Это тестовое задание, так что не будем <br />
            углубляться в глубины проблем фармацевтов.
          </p>
        </div>
        <img
          src="./assets/image.png"
          width="500"
          height="500"
          alt=""
          style="overflow: visible"
        />
      </div>
    </div>
    <div v-else id="nav">
      <div id="nav__top">
        <button class="radial">
          <img src="./assets/homesvg.svg" alt="" />
        </button>

        <button class="radial">
          <img src="./assets/refreshsvg.svg" alt="" />
        </button>
      </div>
      <div id="center">
        <div><h2>Параметры:</h2></div>

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
    <div id="main">
      <GameCardStack
        :cards="visibleCards"
        @cardAccepted="handleCardAccepted"
        @cardRejected="handleCardRejected"
        @cardSkipped="handleCardSkipped"
        @hideCard="removeCardFromDeck"
      />
      <div id="main_bottom" v-if="visibleCards.length > 0">
        <a
          onclick="handleCardAccepted"
          v-on:click="
            handleCardRejected();
            removeCardFromDeck();
          "
          >Препарат 1</a
        >
        <a
          v-on:click="
            handleCardAccepted();
            removeCardFromDeck();
          "
          >Препарат 2</a
        >
        <a
          v-on:click="
            handleCardSkipped();
            removeCardFromDeck();
          "
          >Препарат 3</a
        >
      </div>
      <div v-else style="display: none"></div>
    </div>
  </div>
</template>

<script>
import GameCardStack from "./components/GameCardStack";

export default {
  name: "App",
  components: {
    GameCardStack,
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
        {
          class: "Марія, 19 років",
          src: "1-Smart 2.jpg",
          text:
            "Бабуся приймає брендовий препарат від болю в суглобах, він допомагає, але занадто дорогий. У Вас є якісний аналог з нижчою ціною? Якщо ні — давайте бренд.",
        },
        {
          class: "Степан, 61 рік",
          src: "8-Poor 2.jpg",
          text:
            "Спросоння відсунув гарячий чайник рукою та обпікся. У Вас всі ліки від опіків такі дорогі? Можна хороший препарат недорого?",
        },
        {
          class: "Любов, 58 років",
          src: "3-Smart 1.jpg",
          text:
            "Лікар призначив препарат від артеріальної гіпертензії, а бренд дорого коштує. Тому мені потрібен аналог з хорошою ефективністю та приємною ціною.",
        },
        {
          class: "Олександр, 20 років",
          src: "4-Smart 1.jpg",
          text:
            "Порекомендуйте ефективний препарат від болю в горлі за розумну ціну.",
        },
        {
          class: "Ірина, 55 років",
          src: "5-Smart 1.jpg",
          text:
            "У мене часто невралгії, лікар призначив вітаміни групи В. Мені потрібен якісний аналог за прийнятною ціною.",
        },
      ],
      swipeAccept: 0,
      swipeRejected: 0,
      swipeSkipped: 0,
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
    },
  },
};
</script>

<style lang="scss">
@import "./styles/mixins.scss";
#app {
  display: flex;
  justify-content: center;
  width: 100vw;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  text-align: center;
}
#start {
  max-width: 1440px;
  display: flex;
  position: fixed;
  background-image: url("./assets/start_bg.png");
  background-repeat: no-repeat;
  background-size: cover;
  z-index: 999;
  width: 100vw;
  height: 100vh;
}

#end {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;

  padding-left: 30px;
  align-items: flex-start;
  position: fixed;
  background: #ffffff;
  background-repeat: no-repeat;
  background-size: cover;
  z-index: 999;
  width: 100vw;
  height: 100vh;
  p:first-child {
    margin-top: 100px;
  }
}

#circle {
  border-radius: 50%;
  background: linear-gradient(63.53deg, #2d8550 16.62%, #5e6ec2 83.38%);
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 560px;
  height: 560px;

  text-align: center;
  p {
    text-align: left;
    color: white;
  }
  p:nth-child(1) {
    text-align: left;
    text-transform: uppercase;

    opacity: 0.59;
    font-size: 16px;
    line-height: 40, 73px;
    margin-top: 80px;
    margin-bottom: 29px;
  }
  p:nth-child(2) {
    font-size: 35px;
    margin-bottom: 100px;
    font-weight: bolder;
    letter-spacing: 3px;
    line-height: 40, 73px;
  }
  a {
    color: #8e9ad5;
    font-size: 26px;
    font-weight: 600;
    padding: 15px 60px;
    background: white;
    border-radius: 50px;
    cursor: pointer;
  }
}

#nav div:nth-child(2) #clickStat p {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 35px;
  font-weight: 400;
  color: #424242;
  line-height: 35px;
  width: 45%;
  margin: 10px;
  /* padding: 15px; */
  text-align: center;
  background: #fff;
  border-radius: 50px;
}
#main {
  display: flex;
  flex-direction: column-reverse;

  width: 970px;
}
#main_top {
  position: relative;
  width: 100%;
  height: auto;
}
#main_bottom {
  position: relative;
  height: 74px;
  a {
    font-size: 18px;
    padding: 20px 50px;
    text-decoration: none;
    color: white;
    font-weight: 500;
  }
  a:nth-child(1) {
    background: linear-gradient(266.19deg, #8049c7 0%, #ca57fd 100%);
    border-radius: 100px;
  }
  a:nth-child(2) {
    background: linear-gradient(266.19deg, #169ae4 0%, #0cc4fa 100%);
    border-radius: 100px;
    margin: 0 40px;
  }
  a:nth-child(3) {
    background: linear-gradient(
      90deg,
      #ffd748 0.02%,
      rgba(195, 199, 11, 0.96) 99.97%,
      #cac6ab 99.98%,
      #d3e9e1 99.99%
    );
    border-radius: 100px;
  }
}
#nav {
  position: relative;
  display: flex;
  max-width: 40vw;
  flex-direction: column;
  justify-content: space-between;
  background-image: url(/img/pink_bg.43954c21.png);
  width: 470px;
  height: 100vh;
  background-size: cover;
  &__top {
    display: flex;
    justify-content: flex-start;
  }
  #center {
    display: flex;
    flex-direction: column;
    h2 {
      padding-left: 40px;
    }
  }

  h2 {
    text-align: left;
    color: white;
  }
  div:nth-child(3) {
    background: #fff5;
    color: white;
    height: 134px;
    display: flex;
    align-items: center;
    justify-content: center;

    p {
      text-transform: uppercase;
      font-weight: 400 !important;
      letter-spacing: 0px;
      font-size: 35px;
      line-height: 110, 25px;
      font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS",
        sans-serif;
      text-shadow: 5px 0 27px rgb(92, 92, 92);
    }
  }
  div:nth-child(2) {
    position: relative;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    #clickStat {
      p {
        font-size: 45px;
        font-weight: 400;
        color: #424242;
        line-height: 70px;
        width: 45%;
        margin: 10px;
        padding: 15px;
        text-align: center;
        background: #fff;
        border-radius: 50px;
      }
      img {
        transform: translate(-30px, 3px);
      }
    }
  }

  #percentStat {
    display: flex im !important;
    width: 100%;
  }

  div#percentStat {
    font-size: 32px;
    display: flex;
    flex-direction: row;
  }
  #clickStat {
    p {
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
    margin-left: 40px;
    border-radius: 50%;
    background: rgb(255, 255, 255);
  }
}
#percents {
  display: flex;
  justify-content: center;
  width: 700px;
  font-size: 48px;
  letter-spacing: 5px;
}
#drug {
  width: 700px;
  word-spacing: 10px;
  letter-spacing: 3px;
  font-size: 13px;
  font-weight: 100;
}

hr {
  border-top: 2px solid #8e9ad5;
  margin: 40px;
}
#wtf {
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  padding-left: 170px;
  font-size: 32px;
  line-height: 35px;
  letter-spacing: 0.02em;
  text-align: left;
  color: #8e9ad5;
}
#thistest {
  left: 9.03%;
  right: 50.69%;
  top: 54.69%;
  text-align: justify;
  bottom: 38.48%;
  margin-top: 20px;
  padding-left: 170px;
  font-family: Avenir Next Cyr;
  font-size: 24px;
  line-height: 29px;

  /* teva_dark gray */

  color: #424242;
}
</style>
