<template>
  <v-app>
    <!-- Navbar -->
    <AppBar />
    <v-main>
      <Snackbar></Snackbar>
      <nuxt />
    </v-main>
    <DialogLogin />
    <DialogRegister />
  </v-app>
</template>

<script>
import AppBar from '~/components/Header/Bar/AppBar.vue'
export default {
  components: { AppBar },
  data() {
    return {
      dialogLogin: false,
    }
  },
  // created() {
  //   this.$supabase.auth.onAuthStateChange(async (event, session) => {
  //     await this.request({ event, session })
  //   })
  // },
  mounted() {
    const theme = localStorage.getItem('useDarkTheme')
    if (theme) {
      if (theme === 'true') {
        this.$vuetify.theme.dark = true
      } else this.$vuetify.theme.dark = false
    }
  },
//   methods: {
//     async handleRedirect(event) {
//       switch (event) {
//         case 'SIGNED_IN': {
//           const data = await this.$axios.$post('/api/rest/user')
//           const { user } = data
//           if (user) {
//             this.$store.commit('auth/setUser', user)
//             this.show = false
//             const { data, error } = await this.$supabase
//               .from('userinfo')
//               .select()
//               .eq('uuid', user.id)
//             if (error) {
//               this.$notifier.showMessage({
//                 content: error.message,
//                 color: 'error',
//               })
//             } else if (data) {
//               const { error } = await this.$supabase.auth.update({
//                 data: data[0],
//               })
//               if (error) {
//                 console.error(error)
//               }
//               this.$notifier.showMessage({
//                 content: 'Vous êtes connecté !',
//                 color: 'success',
//               })
//             }
//           }
//           break
//         }
//         case 'SIGNED_OUT': {
//           const data = await this.$axios.$post('/api/rest/user')
//           const { user = null } = data

//           if (!this.$store.state.auth.user !== user) {
//             this.$store.commit('auth/setUser', user)
//           }
//           this.$notifier.showMessage({
//             content: 'Déconnexion.',
//             color: 'success',
//           })
//           this.$router.push('/')
//           break
//         }
//         default: {
//           console.log({ event })
//           break
//         }
//       }
//     },
//     async request({ event, session }) {
//       if (!event) {
//         throw new Error('Missing event')
//       }
//       await this.$axios
//         .post('/api/rest/auth', { event, session })
//         .then(() => {
//           this.handleRedirect(event)
//         })
//         .catch((error) => console.error(error))
//     },
//   },
}
</script>

<style>
.theme--dark :not(pre) > code[class*='language-'],
pre[class*='language-'] {
  background: #272727;
}

.theme--dark.v-application code {
  background-color: rgba(255, 255, 255, 0);
  color: white;
}

.v-application code,
.v-application kbd {
  font-size: 100%;
}
</style>
