<template>
  <v-app dark>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <span v-if="name">{{ name }}</span>
      <v-btn
        v-if="this.$auth.loggedIn"
        color="primary"
        class="ml-4 text-none"
        @click="logout"
      >
        Se déconnecter
      </v-btn>
    </v-app-bar>
    <v-content>
      <v-container fill-height>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
      :fixed="fixed"
      app
    >
      <v-row style="min-height=60px;max-height:100px;" align="center" class="my-1">
        <v-col sm="6">
          <span>Réalisation : <a href="https://www.cstip.ulaval.ca/">Centre de services en TI et en pédagogie</a></span>
        </v-col>
        <v-col sm="6" align="right">
          <v-btn
            color="primary"
            class="text-none"
            href="mailto:aide@cstip.ulaval.ca"
          >
            aide@cstip.ulaval.ca
          </v-btn>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      fixed: false,
      title: 'Nom de l\'application'
    }
  },
  computed: {
    name () {
      if (this.$auth.isLoggedIn) {
        return this.$auth.user.name
      } else {
        return ''
      }
    }
  },
  methods: {
    logout () {
      this.$auth.logout()
    }
  }
}
</script>
