<template>
  <v-dialog v-model="show" width="500" @click:outside="show = false">
    <v-card>
      <v-card-title> S'inscrire </v-card-title>
      <v-card-text>
        <v-container>
          <v-alert
            v-show="alertMessage"
            :color="alertType"
            :type="alertType"
            dense
            >{{ alertMessage }}</v-alert
          >
          <v-text-field v-model="inputEmail" label="Email*"></v-text-field>
          <v-text-field v-model="inputUsername" label="Nom d'utilisateur*">
          </v-text-field>
          <v-text-field
            v-model="inputPassword"
            label="Mot de passe*"
            type="password"
          ></v-text-field>
          <v-text-field
            v-model="inputConfirmPassword"
            label="Confirmation du mot de passe*"
            type="password"
          ></v-text-field
        ></v-container>
      </v-card-text>

      <v-divider></v-divider>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="primary" text @click="createUser()"> S'inscrire </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: 'DialogRegister',
  data() {
    return {
      inputEmail: null,
      inputUsername: null,
      inputPassword: null,
      inputConfirmPassword: null,
      show: false,
      alertType: 'error',
      alertMessage: '',
      alertShow: false,
    }
  },
  created() {
    this.$nuxt.$on('dialog-register', (val) => {
      this.show = val
    })
  },
  methods: {
    createUser() {
      console.log('create user')
    },
  },
}
</script>
