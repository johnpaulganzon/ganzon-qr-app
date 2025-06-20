<template>
    <div class="d-flex align-center justify-center" style="height: 100vh;">
        <v-card width="500"> 
        <h1 class="d-flex align-cneter justify-center">SIGN IN PAGE</h1>
        <v-text-field placeholder="Email" class=""></v-text-field>
        <v-text-field label="Password"></v-text-field>


        <v-button class="d-flex align-cneter justify-center"> log in </v-button>
 

        </v-card>
    </div>
</template>
<script>
export default {
    layout: "auth" 
}
</script>