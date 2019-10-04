<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Card</span>
        <span class="font-weight-light">bords</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn :to="{ name: 'register' }">Register</v-btn>
      <v-btn :to="{ name: 'about' }">Login</v-btn>
    </v-app-bar>

    <v-content>
      <router-view>

      </router-view>
    </v-content>
    
  </v-app>
</template>
