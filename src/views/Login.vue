<template>
  <v-container fluid fill-height>
    <main-header/>
    <v-layout align-center justify-center>
      <v-flex xs12 sm8 md5>
        <v-card class="elevation-15">
          <v-toolbar dark>
            <v-toolbar-title>Sign in form</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
            <v-form ref="form" v-model="valid" lazy-validation>
              <v-text-field
                v-model="email"
                color="grey"
                prepend-icon="person"
                name="email"
                label="Email"
                type="email"
                :rules="emailRules"
              ></v-text-field>
              <v-text-field
                v-model="password"
                color="grey"
                prepend-icon="lock"
                name="password"
                label="Password"
                type="password"
                :rules="passwordRules"
              ></v-text-field>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn :disabled="!valid" class="white" @click="onSubmit">Submit</v-btn>
          </v-card-actions>
        </v-card>
        
      </v-flex>
    </v-layout>
    <v-snackbar
          color="red"
          v-model= 'snackbar'
          :bottom="true"
          @click="closeError"
          :multi-line="true"
          :timeout="5000"
          :value="true"
        >
         wrong password or login
          <v-btn ripple color="error" @click="closeError">Close</v-btn>
        </v-snackbar>
  </v-container>

</template>

<script>
import mainHeader from "../components/header";
import axios from "axios";
export default {
  data() {
    return {
      snackbar: false,
      email: "",
      password: "",
      valid: false,
      emailRules: [ //Валидация
        v => !!v || "E-mail is required",
        v => /.+@.+/.test(v) || "E-mail must be valid"
      ],
      passwordRules: [
        v => !!v || "Password is required",
        v => (v && v.length >= 3) || "Password must be more than 3 characters"
      ]
    };
  },
  methods: {
    closeError(){
      this.snackbar = false
    },
    async onSubmit() {
      if (this.$refs.form.validate()) {
        const user = {
          username: this.email,
          password: this.password
        };
       
        const res = await axios
          .post("/auth/login", user)
           .catch(err => {
            console.log("---", err);
            this.snackbar = true;
          });
         
      }
    }
  },
  computed: {},
  components: {
    mainHeader
  }
};
</script>
