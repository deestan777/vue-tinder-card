<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Welcome to Vuetify
        </h1>

        <p class="subheading font-weight-regular">
          For help and collaboration with other Vuetify developers,
          <br />please join our online
          <a href="https://community.vuetifyjs.com" target="_blank"
            >Discord Community</a
          >
        </p>
      </v-col>

      <v-col class="mb-5" cols="12">
        <h2 class="headline font-weight-bold mb-3">
          What's next?
        </h2>

        <v-row justify="center">
          <a
            v-for="(next, i) in whatsNext"
            :key="i"
            :href="next.href"
            class="subheading mx-3"
            target="_blank"
          >
            {{ next.text }}
          </a>
        </v-row>
      </v-col>

      <v-col class="mb-5" cols="12">
        <h2 class="headline font-weight-bold mb-3">
          Important Links
        </h2>

        <v-row justify="center">
          <a
            v-for="(link, i) in importantLinks"
            :key="i"
            :href="link.href"
            class="subheading mx-3"
            target="_blank"
          >
            {{ link.text }}
          </a>
        </v-row>
      </v-col>

      <v-col class="mb-5" cols="12">
        <h2 class="headline font-weight-bold mb-3">
          Ecosystem
        </h2>

        <v-row justify="center">
          <a
            v-for="(eco, i) in ecosystem"
            :key="i"
            :href="eco.href"
            class="subheading mx-3"
            target="_blank"
          >
            {{ eco.title }}<br />
            {{ eco.description }}<br />
            {{ eco.price }}{{ eco.currency }}
          </a>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
    ecosystem: [
      {
        id: 0,
        category: "Men",
        title: "Nike Yezzy 2",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/0.jpg",
        images: ["../img/products/011.jpg", "../img/products/0111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 1,
        category: "Men",
        title: "Nike Alpha",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/01.jpg",
        images: ["../img/products/011.jpg", "../img/products/0111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 2,
        category: "Men",
        title: "Nike Beta",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/02.jpg",
        images: ["../img/products/022.jpg", "../img/products/0222.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 3,
        category: "Men",
        title: "Nike Delta",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/03.jpg",
        images: ["../img/products/033.jpg", "../img/products/0333.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 4,
        category: "Men",
        title: "Nike Gamma",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/04.jpg",
        images: ["../img/products/044.jpg", "../img/products/0444.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 5,
        category: "Men",
        title: "Nike Custom",
        description: "",
        price: 240,
        currency: "$",
        mainImage: "../img/products/05.jpg",
        images: ["../img/products/055.jpg", "../img/products/0555.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 6,
        category: "Men",
        title: "Nike Super",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/06.jpg",
        images: ["../img/products/066.jpg", "../img/products/0666.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 7,
        category: "Men",
        title: "Nike Mega",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/07.jpg",
        images: ["../img/products/077.jpg", "../img/products/0777.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 8,
        category: "Men",
        title: "Nike Awesome",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/08.jpg",
        images: ["../img/products/088.jpg", "../img/products/0888.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 9,
        category: "Men",
        title: "Nike Amasing",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/09.jpg",
        images: ["../img/products/099.jpg", "../img/products/0999.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 10,
        category: "Woman",
        title: "Nike Purple",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/g1.jpg",
        images: ["../img/products/g11.jpg", "../img/products/g111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 11,
        category: "Woman",
        title: "Nike Elegant",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/g2.jpg",
        images: ["../img/products/g22.jpg", "../img/products/g222.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 12,
        category: "Woman",
        title: "Nike Pretty",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/g3.jpg",
        images: ["../img/products/g33.jpg", "../img/products/g333.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 13,
        category: "Woman",
        title: "Nike Cutty",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/g4.jpg",
        images: ["../img/products/g44.jpg", "../img/products/g444.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 14,
        category: "Woman",
        title: "Nike Pussy",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/g5.jpg",
        images: ["../img/products/g55.jpg", "../img/products/g555.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 15,
        category: "Woman",
        title: "Nike Cunt",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/g6.jpg",
        images: ["../img/products/g66.jpg", "../img/products/g666.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 16,
        category: "Woman",
        title: "Nike Curva",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/g7.jpg",
        images: ["../img/products/g77.jpg", "../img/products/g777.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 17,
        category: "Woman",
        title: "Nike Kurwa",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/g8.jpg",
        images: ["../img/products/g88.jpg", "../img/products/g888.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 18,
        category: "Woman",
        title: "Nike Purple",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/g9.jpg",
        images: ["../img/products/g99.jpg", "../img/products/g999.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 19,
        category: "Kids",
        title: "Nike Little Foot",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/k1.jpg",
        images: ["../img/products/k11.jpg", "../img/products/k111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 20,
        category: "Kids",
        title: "Nike Puppy",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/k2.jpg",
        images: ["../img/products/k22.jpg", "../img/products/k222.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 21,
        category: "Kids",
        title: "Nike Kitty",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/k3.jpg",
        images: ["../img/products/k33.jpg", "../img/products/k333.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 22,
        category: "Kids",
        title: "Nike Endy",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/k4.jpg",
        images: ["../img/products/k44.jpg", "../img/products/k444.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 23,
        category: "Kids",
        title: "Nike Rugrats",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/k5.jpg",
        images: ["../img/products/k55.jpg", "../img/products/k555.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 24,
        category: "Kids",
        title: "Nike Monkey",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/k6.jpg",
        images: ["../img/products/k66.jpg", "../img/products/k666.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 25,
        category: "Kids",
        title: "Nike Pinokio",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/k7.jpg",
        images: ["../img/products/k77.jpg", "../img/products/k777.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 26,
        category: "Kids",
        title: "Nike Donkey",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/k8.jpg",
        images: ["../img/products/k88.jpg", "../img/products/k888.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 27,
        category: "Kids",
        title: "Nike Fiona",
        description: "Bertouloume",
        price: 240,
        currency: "$",
        mainImage: "../img/products/k9.jpg",
        images: ["../img/products/k99.jpg", "../img/products/k999.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 28,
        category: "Coming Soon",
        title: "Nike Back to the future",
        description: "Doc's gift to Marty",
        price: 240,
        currency: "$",
        mainImage: "../img/products/s1.jpg",
        images: ["../img/products/s11.jpg", "../img/products/s111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 29,
        category: "Coming Soon",
        title: "Robotic shoes",
        description: "Sync it with your smartphone",
        price: 240,
        currency: "$",
        mainImage: "../img/products/s2.jpg",
        images: ["../img/products/s11.jpg", "../img/products/s111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 30,
        category: "Coming Soon",
        title: "Nike cyber goth",
        description: "Woow",
        price: 240,
        currency: "$",
        mainImage: "../img/products/s3.jpg",
        images: ["../img/products/s11.jpg", "../img/products/s111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 31,
        category: "Coming Soon",
        title: "Nike chair edition",
        description: "Don't try to sit on this",
        price: 240,
        currency: "$",
        mainImage: "../img/products/s4.jpg",
        images: ["../img/products/s11.jpg", "../img/products/s111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 32,
        category: "Coming Soon",
        title: "Nike elegant ",
        description: "Space trooper summer edition",
        price: 240,
        currency: "$",
        mainImage: "../img/products/s5.jpg",
        images: ["../img/products/s11.jpg", "../img/products/s111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 33,
        category: "Coming Soon",
        title: "Nike Bender",
        description: "Bend it all!",
        price: 240,
        currency: "$",
        mainImage: "../img/products/s6.jpg",
        images: ["../img/products/s11.jpg", "../img/products/s111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 34,
        category: "Coming Soon",
        title: "Nike Back to the future",
        description: "Doc's gift to Mcfly",
        price: 240,
        currency: "$",
        mainImage: "../img/products/s7.jpg",
        images: ["../img/products/s11.jpg", "../img/products/s111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 35,
        category: "Coming Soon",
        title: "Nike Back to the future",
        description: "Doc's gift to Mcfly",
        price: 240,
        currency: "$",
        mainImage: "../img/products/s8.jpg",
        images: ["../img/products/s11.jpg", "../img/products/s111.jpg"],
        size: [36, 37, 38, 39, 40]
      },
      {
        id: 36,
        category: "Coming Soon",
        title: "Nike Back to the future",
        description: "Doc's gift to Mcfly",
        price: 240,
        currency: "$",
        mainImage: "../img/products/s9.jpg",
        images: ["../img/products/s11.jpg", "../img/products/s111.jpg"],
        size: [36, 37, 38, 39, 40]
      }
    ],
    importantLinks: [
      {
        text: "Documentation",
        href: "https://vuetifyjs.com"
      },
      {
        text: "Chat",
        href: "https://community.vuetifyjs.com"
      },
      {
        text: "Made with Vuetify",
        href: "https://madewithvuejs.com/vuetify"
      },
      {
        text: "Twitter",
        href: "https://twitter.com/vuetifyjs"
      },
      {
        text: "Articles",
        href: "https://medium.com/vuetify"
      }
    ],
    whatsNext: [
      {
        text: "Explore components",
        href: "https://vuetifyjs.com/components/api-explorer"
      },
      {
        text: "Select a layout",
        href: "https://vuetifyjs.com/getting-started/pre-made-layouts"
      },
      {
        text: "Frequently Asked Questions",
        href: "https://vuetifyjs.com/getting-started/frequently-asked-questions"
      }
    ]
  })
};
</script>
