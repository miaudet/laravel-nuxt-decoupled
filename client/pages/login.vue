<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <v-form
        ref="form"
      >
        <v-alert v-if="error" type="error">
          {{ error }}
        </v-alert>
        <v-card>
          <v-card-title class="headline">
            Connexion
          </v-card-title>
          <v-card-text>
            <v-text-field
              v-model="email"
              color="blue lighten-2"
              label="Courriel"
              required
            />
            <v-text-field
              v-model="password"
              :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
              :type="showPassword ? 'text' : 'password'"
              color="blue lighten-2"
              label="Mot de passe"
              required
              @click:append="showPassword = !showPassword"
            />
          </v-card-text>
          <v-card-actions>
            <v-spacer />
            <v-btn
              color="primary"
              class="mr-4"
              @click="login"
            >
              Se connecter
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-form>
    </v-flex>
  </v-layout>
</template>

<script>

export default {
  data () {
    return {
      showPassword: false,
      email: '',
      password: '',
      error: ''
    }
  },
  methods: {
    async login () {
      this.error = ''
      try {
        await this.$auth.loginWith('local', {
          data: {
            email: this.email,
            password: this.password
          }
        })
      } catch (e) {
        this.error = e.response.data.message
      }
    }
  }
}
</script>
