<template>
  <v-app>
    <v-app-bar color="primary" class="flex-grow-0" app light>
      <v-app-bar-title></v-app-bar-title>
    </v-app-bar>
    <template v-if="!$auth.loggedIn">
        <LoginComponent />
    </template>
    <Layout v-else />
  </v-app>
</template>

<script>
import MenuLayout from '../layouts/menu.vue'
import LoginComponent from '../components/LoginComponent.vue'

export default {
  name: 'Index',
  components: {
    MenuLayout,
    LoginComponent
  }
};
</script>
