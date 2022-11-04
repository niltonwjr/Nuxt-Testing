<template>
  <v-row justify="center" align="center">
    <v-btn @click="test()">Captcha key</v-btn>
    <recaptcha />
  </v-row>
</template>

<script>
export default {
  name: "loginPage",
  methods: {
    async test() {
      try {
        const token = await this.$recaptcha.getResponse();
        console.log("ReCaptcha token:", token);

        // send token to server alongside your form data

        // at the end you need to reset recaptcha
        await this.$recaptcha.reset();
      } catch (error) {
        console.log("Login error:", error);
      }
    },
  },
};
</script>
