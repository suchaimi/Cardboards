<template>
  <div class="register">
    <v-container fluid>
      <v-layout column align-center>
        <v-card width="400" class="mx-auto">
          <form v-model="valid" @submit.prevent="register" @keydown.prevent.enter>
            <v-text-field v-model="user.username" :rules="simpleRules" label="Username" required></v-text-field>
            <v-text-field v-model="user.display" :rules="simpleRules" label="Display Name" required></v-text-field>
            <v-text-field
              v-model="user.password"
              :rules="simpleRules"
              label="Password"
              type="password"
              required
            ></v-text-field>
            <v-text-field
              v-model="user.cpassword"
              :rules="confirmPasswordRules"
              label="Confirm Password"
              type="password"
              required
            ></v-text-field>

            <v-text-field v-model="user.avatar" :rules="simpleRules" label="Avatar" required></v-text-field>

            <v-btn type="submit" class="mr-4">submit</v-btn>
          </form>
        </v-card>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "register",
  data: (vm) => ({
    valid: false,
    user: {
      username: "",
      password: "",
      cpassword: "",
      display: "",
      avatar: ""
    },
    simpleRules: [value => !!value || "Required field"],
    confirmPasswordRules: [cpassword => cpassword === vm.user.password || 'Password must match']
  }),
  components: {},
  methods: {
    register() {}
  }
};
</script>