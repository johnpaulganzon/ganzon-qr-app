<template>
    <div class="d-flex align-center justify-center" style="height: 100vh;">
        <v-card width="500" class="px-8 py-10 textcenter">
            <h2 class="d-flex align-cneter justify-center">Log in Page</h2>
            <v-form>
                <v-text-field label="Email"
                outlined rounded prepend-inner-icon ="mdi-email"></v-text-field>
                <v-text-field label="Password"
                outlined rounded prepend-inner-icon="mdi-lock" type="password"></v-text-field>

                <v-btn color="blue" rounded block> Log in </v-btn>
                <div class="d-flex align-center justify-center"> OR </div>
                <v-btn color="red" @click="signinWithGoogle()" class="text-capitalize" rounded block><v-icon left>mdi-google</v-icon>Sign in with google</v-btn>
            </v-form>
        </v-card>
        </div>
        </template>
        <script>
        export default {
            layout: "auth",
            middleware: "guest",
            methods:{
                signinWithGoogle(){
                    this.$auth.loginWith('google')
                }
            }
            }
            </script>