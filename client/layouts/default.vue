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
        class="ml-4"
        @click="logout"
      >
        Se déconnecter
      </v-btn>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
      :fixed="fixed"
      app
    >
      <span>&copy; 2019</span>
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
