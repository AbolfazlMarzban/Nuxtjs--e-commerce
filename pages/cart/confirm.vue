<template>
  <div>
    <Nav />
    <div v-if="$store.state.cart.cart.length === 0" class="text-center">
      <p>No Items Just Yet! Keep Shopping :)</p>
    </div>
    <v-container>
      <div class="mb-3" v-if="$store.state.cart.cart.length > 0">
        <v-btn nuxt to="/cart" min-width="150" min-height="45" depressed
          >Back</v-btn
        >
        <v-btn @click="proccess" min-width="150" min-height="45" color="primary"
          >Complete!</v-btn
        >
      </div>
      <v-form lazy-validation ref="form" class="mt-10">
        <p class="font-weight-bold">Personal & Delivery</p>
        <v-row>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="email"
              :rules="[rules.required, rules.email]"
              outlined
              label="Email"
              type="email"
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="name"
              :rules="[rules.required]"
              outlined
              label="Full Name"
              type="text"
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="phone"
              :rules="[rules.required]"
              outlined
              label="phone"
              type="tel"
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="address"
              :rules="[rules.required]"
              outlined
              label="Address"
              type="text"
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="city"
              :rules="[rules.required]"
              outlined
              label="City"
              type="text"
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="country"
              :rules="[rules.required]"
              outlined
              label="Country"
              type="text"
            ></v-text-field>
          </v-col>
        </v-row>
        <p class="font-weight-bold">Credit Card</p>
        <v-row>
          <v-col cols="12" md="12">
            <v-text-field
              v-model="cc"
              :rules="[rules.required]"
              outlined
              label="Credit Card Number"
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="6">
            <v-text-field
              v-model="expdate"
              :rules="[rules.required]"
              outlined
              label="Exp date"
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="6">
            <v-text-field
              v-model="ccv"
              :rules="[rules.required]"
              outlined
              label="Security code/CVV"
            ></v-text-field>
          </v-col>
        </v-row>
      </v-form>
    </v-container>
  </div>
</template>

<script>
import Nav from "~/components/Nav.vue";
export default {
  components: { Nav },
  data() {
    return {
      email: null,
      name: null,
      phone: null,
      address: null,
      city: null,
      country: null,
      cc: null,
      expdate: null,
      cvv: null,
      rules: {
        required: (v) => !!v || "Required",
      },
    };
  },
  methods: {
    async proccess() {
      if (!this.$refs.form.validate()) return;
      await this.$swal({
        title: "Processing your Order",
        icon: "info",
        allowEscapeKey: false,
        allowOutsideKey: false,
        timer: 3000,
        timerProgressBar: true,
        text: "Please Wait",
        showConfirmButton: false,
      });

      await this.$swal({
        title: "Order Complete!",
        icon: "success",
        allowEscapeKey: false,
        allowOutsideKey: false,
        timer: 4000,
        timerProgressBar: true,
        text: "Thank You So Much...",
        showConfirmButton: false,
      });
      //Remove Items From Cart
      this.$store.commit("cart/ClearCart");
      this.$router.push("/");
    },
  },
};
</script>

<style></style>
