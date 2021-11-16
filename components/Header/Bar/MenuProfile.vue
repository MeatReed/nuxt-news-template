<template>
  <v-menu bottom min-width="200px" rounded offset-y>
    <template #activator="{ on }">
      <v-btn icon tile v-on="on">
        <v-avatar color="primary" size="38">
          <span class="white--text">PD</span>
        </v-avatar>
      </v-btn>
    </template>
    <v-list v-if="$store.state.auth.user">
      <v-list-item-content class="justify-center">
        <div class="mx-auto text-center">
          <v-avatar color="primary" size="38">
            <span class="white--text">PD</span>
          </v-avatar>
          <h3>{{ $store.state.auth.user.user_metadata.username }}</h3>
          <v-divider class="my-3"></v-divider>
        </div>
      </v-list-item-content>
      <v-list-item link nuxt to="/profile">
        <v-list-item-title>Mon Compte</v-list-item-title>
      </v-list-item>
      <v-list-item link>
        <v-list-item-title @click="signOut()">Se déconnecter</v-list-item-title>
      </v-list-item>
    </v-list>
    <v-list v-else>
      <v-list-item-content>
        <div class="text-center">
          <v-avatar color="primary" size="38">
            <span class="white--text">PD</span>
          </v-avatar>
          <h3>Non connecté</h3>
        </div>
      </v-list-item-content>
      <v-list-item link>
        <v-list-item-title @click="$nuxt.$emit('dialog-login', true)"
          >Se connecter</v-list-item-title
        >
      </v-list-item>
      <v-list-item link>
        <v-list-item-title @click="$nuxt.$emit('dialog-register', true)"
          >S'inscrire</v-list-item-title
        >
      </v-list-item>
    </v-list>
  </v-menu>
</template>

<script>
export default {
  name: 'MenuProfile',
  methods: {
    async signOut() {
      const { error } = await this.$supabase.auth.signOut()
      if (error) {
        // Handle error
        this.$notifier.showMessage({
          content: error.message,
          color: 'error',
        })
      }
    },
  },
}
</script>
