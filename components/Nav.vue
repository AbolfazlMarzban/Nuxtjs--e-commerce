<template>
  <div>
    <v-app-bar
      color="surface"
      height="80"
      class="el"
      app
      :style="{ padding: $vuetify.breakpoint.mdAndUp ? '0px 100px' : '' }"
    >
      <v-toolbar-title
        class="text-md-h5 font-weight-bold pointer"
        @click="$router.push('/')"
      >
        Abolfazl Marzban Online Shop
      </v-toolbar-title>
      <v-spacer></v-spacer>
        <v-btn icon nuxt to="/products" class="mx-10">
        <span>shop</span>
        <v-icon size="20">mdi-store-outline</v-icon>
      </v-btn>
      <v-badge
        overlap
        :content="$store.state.cart.cart.length"
        v-if="$store.state.cart.cart.length > 0"
        class="mx-10"
      >
        <v-btn nuxt to="/cart" icon>
          <span>cart</span>
          <v-icon size="20">mdi-cart-outline</v-icon>
        </v-btn>
      </v-badge>
      <v-btn nuxt to="/cart" v-else icon>
        <span>cart</span>
        <v-icon size="20">mdi-cart-outline</v-icon>
      </v-btn>
      <v-divider vertical class="mx-md-5 mx-2"></v-divider>
      <v-btn @click="toggleTheme" icon class="mx-10">
        <span>change Theme</span>
        <v-icon size="20">mdi-brightness-7</v-icon>
      </v-btn>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  methods: {
    toggleTheme() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    },
  },
};
</script>

<style>

</style>
