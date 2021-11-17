<template>
  <v-container>
    <v-card>
      <v-img
        src="img/banner.jpg"
        height="250px"
      ></v-img>
      <v-card-text>
        <v-container>
          <v-row class="mb-2" justify="center">
            <h1>Titre article 1</h1>
          </v-row>
          <v-row class="fill-height mb-2" align="center" justify="center"
            ><v-avatar size="30px">
              <img
                alt="Avatar"
                src="img/avatar.jpg"
            /></v-avatar>
            <span class="pl-2">TIーム</span>
            <span class="pl-2">|</span>
            <span class="pl-2">18/01/2021</span>
          </v-row>
          <nuxt-content :document="page" />
        </v-container>
      </v-card-text>
    </v-card>
    <h1>Commentaire</h1>
    <v-card v-for="i in 10" :key="i" class="mt-2">
      <v-card-text>
        <v-row>
          <v-col>
            <v-row class="mb-4 fill-height text-center" no-gutters>
              <v-col cols="12">
                <v-avatar size="120px">
                  <v-img
                    alt="Avatar"
                    src="img/banner.jpg"
                  />
                </v-avatar>
              </v-col>
              <v-col cols="12">
                <span class="pl-2">TIーム</span>
              </v-col>
              <v-col cols="12">
                <v-row class="ml-1" justify="center" align="center">
                  <v-chip-group>
                    <v-chip color="blue" x-small> Développeur Web </v-chip>
                  </v-chip-group>
                </v-row>
              </v-col>
            </v-row>
          </v-col>
          <v-col cols="9">
            <v-row>
              <span class="font-weight-black">Editer | 00/00/00</span>
              <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
                Asperiores quo sapiente, quis sequi, blanditiis fugiat delectus
                atque ab ducimus magnam voluptatum rem inventore dolorem? Maiores
                perspiciatis consequatur deserunt pariatur dignissimos.
              </p>
            </v-row>
          </v-col>
        </v-row>
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <span>Info ramdom jsp</span>
      </v-card-actions>
    </v-card>
    <v-card class="mt-2">
      <v-card-text>
        <v-textarea
          outlined
          label="Ecrire un commentaire"
          value="slurp"
        ></v-textarea>
        <v-btn block>Envoyer</v-btn>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const page = await $content('article').fetch()

    return {
      page
    }
  }
}
</script>

<style>
img {
  width: 100%;
}
</style>
