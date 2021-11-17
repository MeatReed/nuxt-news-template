<template>
  <v-container>
    <v-row>
      <v-col>
        <v-carousel
          height="350"
          cycle
          show-arrows-on-hover
          hide-delimiters
          class="rounded-lg"
        >
          <v-carousel-item
            v-for="(item, i) in items"
            :key="i"
            :src="item.src"
            nuxt
            to="/article"
            >
            <v-row
              class="fill-height pl-7 font-weight-black"
              align="end"
              justify="start"
            >
              <div class="title">Article numéro {{ i }}</div>
            </v-row>  
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" xl="8" lg="8" md="12" sm="12">
        <v-card
          v-for="i in 2"
          :key="i"
          class="card_news"
          elevation="0"
        >
          <NuxtLink to="/article">
            <v-img
              class="cover mb-3 rounded-lg"
              width="100%"
              height="300px"
              src="img/banner.jpg"
            />
          </NuxtLink>
          <v-card-text>
            <v-row align="center">
              <h2>Article {{ i }}</h2>
              <v-spacer></v-spacer>
              <v-chip-group>
                <v-chip x-small> tag 1 </v-chip>
                <v-chip x-small> bit </v-chip>
              </v-chip-group>
            </v-row>
            <v-row class="fill-height" align="center"
              ><v-avatar size="30px">
                <img alt="Avatar" src="img/avatar.jpg"
              /></v-avatar>
              <span class="pl-2">Utilisateur</span>
              <span class="pl-2">|</span>
              <span class="pl-2">00/00/0000</span>
            </v-row>
            <v-row>
              <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
                Blanditiis neque facilis vel voluptatem molestiae dolorum sit
                aperiam molestias ullam minima minus illo tenetur eum
                consectetur sapiente maxime, praesentium quia quisquam?
              </p>
            </v-row>
          </v-card-text>
          <v-divider class="pb-6"></v-divider>
        </v-card>
        <v-card
          v-for="i in articleNumber"
          :key="i"
          class="card_news"
          elevation="0"
          to="/article"
        >
          <v-card-text>
            <v-row>
              <v-col v-if="!$vuetify.breakpoint.mobile" class="text-center align-self-center" cols="2">
                <v-avatar size="100px" tile>
                  <v-img class="rounded-lg" alt="Avatar" src="img/banner.jpg"
                /></v-avatar>
              </v-col>
              <v-col :cols="$vuetify.breakpoint.mobile ? 12 : 10" class="d-flex flex-column">
                <v-row align="center">
                  <h2>Article {{ i }}</h2>
                  <v-spacer></v-spacer>
                  <v-chip-group>
                    <v-chip x-small> tag 1 </v-chip>
                    <v-chip x-small> bit </v-chip>
                  </v-chip-group>
                </v-row>
                <v-row class="fill-height" align="center"
                  ><v-avatar size="30px">
                    <img alt="Avatar" src="img/avatar.jpg"
                  /></v-avatar>
                  <span class="pl-2">Utilisateur</span>
                  <span class="pl-2">|</span>
                  <span class="pl-2">00/00/0000</span>
                </v-row>
                <v-row>
                  <p>
                    Lorem ipsum dolor sit amet consectetur adipisicing elit.
                    Blanditiis neque facilis vel voluptatem molestiae dolorum sit
                    aperiam molestias ullam minima minus illo tenetur eum
                    consectetur sapiente maxime, praesentium quia quisquam?
                  </p>
                </v-row>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col v-if="!$vuetify.breakpoint.mobile">
        <v-card width="100%">
          <v-card-title
            >Recommandé <v-spacer></v-spacer
            ><v-btn rounded outlined x-small>Plus</v-btn></v-card-title
          >
          <v-card-text>
            <v-card nuxt to="/article" width="300">
              <v-img
                src="https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg"
                ><v-row
                  class="fill-height pl-7 mt-2 font-weight-black"
                  align="end"
                  justify="start"
                >
                  <p style="color: white">Article numéro 0</p>
                </v-row></v-img
              >
            </v-card>
            <v-list dense>
              <v-list-item-group>
                <v-list-item v-for="i in 4" :key="i" nuxt to="/article">
                  <v-list-item-content>
                    <v-list-item-title>Article {{ i }}</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-item-group>
            </v-list>
          </v-card-text>
        </v-card>
        <v-card class="mt-2" height="200px" width="100%">
          <v-card-title>Informations</v-card-title>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg',
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/sky.jpg',
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg',
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg',
        },
      ],
      articleNumber: 10,
    }
  },
  methods: {
    addArticles() {
      this.articleNumber = this.articleNumber + 10
    },
  },
}
</script>

<style scoped>
.title {
  color: white;
}

.card_news.theme--dark {
  background-color: #121212;
}
</style>
