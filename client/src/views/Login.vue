<template>
<v-container fluid>
  <v-slide-y-transition mode="out-in">
    <v-layout column align-center>
  <div class="text-center">
    <v-progress-circular
      :size="70"
      :width="7"
      color="purple"
      indeterminate
    ></v-progress-circular>
  </div>
  </v-layout>
  </v-slide-y-transition>
</v-container>
</template>

<script>

export default {
  name: 'login',  
}
</script>