<template>
  <v-dialog v-model="show" width="500" @click:outside="show = false">
    <v-card>
      <v-card-title> Se connecter </v-card-title>

      <v-card-text>
        <v-container>
          <v-alert
            v-show="alertMessage"
            :color="alertType"
            :type="alertType"
            dense
            >{{ alertMessage }}</v-alert
          >
          <v-text-field v-model="inputEmail" label="Email*" required>
          </v-text-field>
          <v-text-field
            v-model="inputPassword"
            label="Mot de passe*"
            type="password"
            required
          ></v-text-field
        ></v-container>
      </v-card-text>

      <v-divider></v-divider>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="primary" text @click="signIn()"> Se connecter </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: 'DialogLogin',
  data() {
    return {
      inputEmail: null,
      inputPassword: null,
      show: false,
      alertType: 'error',
      alertMessage: '',
      alertShow: false,
    }
  },
  created() {
    this.$nuxt.$on('dialog-login', (val) => {
      this.show = val
    })
  },
  methods: {
    signIn() {
      console.log('sign In')
    },
  },
}
</script>
