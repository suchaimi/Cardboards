<template>
  <div class="register">
    <v-container fluid>
      <v-layout column align-center>
        <v-row align="center">
          <v-card width="400" class="mx-auto pa-5">
            <v-form
              v-if="!loading"
              v-model="valid"
              @submit.prevent="register()"
              @keydown.prevent.enter
            >
              <v-text-field v-model="user.username" :rules="simpleRules" label="Username" required></v-text-field>
              <v-text-field
                v-model="user.display"
                :rules="simpleRules"
                label="Display Name"
                required
              ></v-text-field>
              <v-text-field
                v-model="user.password"
                :rules="simpleRules"
                label="Password"
                type="password"
                required
              ></v-text-field>
              

              <v-text-field v-model="user.avatar" :rules="simpleRules" label="Avatar" required></v-text-field>

              <v-btn type="submit" class="mr-4" :disabled="!valid">submit</v-btn>
            </v-form>

            <div class="text-center">
              <v-progress-circular v-if="loading" :size="70" :width="7" color="purple" indeterminate></v-progress-circular>
            </div>
          </v-card>
        </v-row>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  name: "register",
  data: vm => ({
    valid: false,
    user: {
      avatar: '',
      display: '',
      username: '',
      password: '',
    },
    simpleRules: [value => !!value || "Required field"],
    confirmPasswordRules: [
      cpassword => cpassword === vm.user.password || "Password must match"
    ]
  }),
  components: {},
  computed: {
    ...mapState("users", { loading: "isCreatePending" })
  },
  methods: {
    register() {
   
      if (this.valid) {
        const data = this.user
        console.log(data);
        const { User } = this.$FeathersVuex;
        const user = new User(data);        
        user.save().then(user => {
          console.log(user);
          this.$router.push('/login')
        })
      }
    }
  }
};
</script>