<template>
    <div class="d-flex align-center justify-center" style="height: 100vh;">
        <v-card width="500"> 
        <h1 class="d-flex align-cneter justify-center">SIGN IN PAGE</h1>
        <v-form>
        <v-text-field label="Email" outlined prepend-inner-icon="mdi-email"></v-text-field>
        <v-text-field label="Password" outlined prepend-inner-icon="mdi-lock"></v-text-field>


        <v-btn color="primary" block> log in </v-btn>
    </v-form>
 

        </v-card>
    </div>
</template>
<script>
export default {
    layout: "auth" 
}
</script>