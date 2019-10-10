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
      <v-card>
        <v-card-title class="headline">
          Bienvenue dans ton application!
        </v-card-title>
        <v-card-text>
          Lorem ipsum
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>

export default {
  data () {
    return {
      id: this.$auth.user.id,
      name: this.$auth.user.name,
      email: this.$auth.user.email
    }
  },
  methods: {
    logout () {
      this.$auth.logout()
    }
  }
}
</script>
