<template>
<v-container fluid fill-height>
     <main-header />
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md5>
            <v-card class="elevation-15">
              <v-toolbar dark>
                <v-toolbar-title>Sign up form</v-toolbar-title>

        
              </v-toolbar>
              <v-card-text>
                <v-form ref="form" v-model="valid" lazy-validation>
                  <v-text-field
                   v-model="email" color="grey" prepend-icon="person"
                   name="email" label="Email" type="email"
                   :rules="emailRules"
                  ></v-text-field>
                  <v-text-field 
                  v-model="password" color="grey" prepend-icon="lock" name="password" 
                  label="Password" type="password" :rules="passwordRules"
                  ></v-text-field>
                  <v-text-field 
                  v-model="confirmPassword" color="grey" prepend-icon="lock" name="confirmPassword" 
                  label="Confirm Password" type="password" :rules="confirmPasswordRules"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                 :disabled="!valid"
                 class="white"
                
                 @click="onSubmit">Create Acc</v-btn>
                 <v-btn
                
                 class="white"
                
                 @click="getThat">Test</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
</template>

<script>
  import mainHeader from '../components/header'
  import axios from 'axios'
export default {
  data () {
    return {
      email: '',
      password: '',
      confirmPassword: '',
      valid: false,
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid'
      ],
      passwordRules: [
        v => !!v || 'Password is required',
        v => (v && v.length >= 3) || 'Password must be more than 3 characters'
      ],
      confirmPasswordRules: [
        v => !!v || 'Password is required',
        v => (v && v.length >= 3) || 'Password must be more than 3 characters',
        v => v == this.password || 'passwords must be the same'
      ]
    }
  },
  methods: {
     onSubmit () {
      if (this.$refs.form.validate()) {
        const user = {
          username: this.email,
          password: this.password
        }
        console.log(user)
        // this.$store.dispatch('userRegistration', user);     
     axios.post('/auth/register', user)
        .then((res) => {
         
          this.$router.push('/')
        })
        .catch((err)=>{
          console.log('something wrong:  ', err)
        })
        console.log('done')
  
  
      }
    }, 
  
  },
  computed: {
   
  },
   components: {
 mainHeader
    }
}
</script>
