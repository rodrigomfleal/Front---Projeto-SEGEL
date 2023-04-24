<template>
  <v-app>
    <v-app-bar color="primary" class="flex-grow-0" app light>
      <v-app-bar-title></v-app-bar-title>
    </v-app-bar>
    <template v-if="!$auth.loggedIn">
        <LoginComponent />
    </template>
    <v-navigation-drawer app color="primary" permanent v-if="$auth.loggedIn">
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6"> SACCE </v-list-item-title>
          <v-list-item-subtitle> UFPE </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      <v-divider></v-divider>
      <v-list dense nav>
        <v-list-item 
          v-for="item in menuItems" 
          :key="item.title" 
          link 
          :to="item.path"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-app>
</template>

<script>
import LoginComponent from '../components/LoginComponent.vue'

export default {
  name: 'App',
  components: {
    LoginComponent
  },
  computed: {
    menuItems() {
      const userType = this.$auth.user.user_type; // Assuming user_type is a field in your user model
      if (userType === 0) { // Manager user
        return [
          { title: 'Dashboard', icon: 'mdi-view-dashboard', path: '/dashboard' },
          { title: 'Minha Conta', icon: 'mdi-account-box', path: '/account' },
          { title: 'Configurações', icon: 'mdi-cog', path: '/settings' },
          { title: 'Criar Área', icon: 'mdi-account-plus', path: '/area'},
        ];
      } else { // Regular user
        return [
          { title: 'Dashboard', icon: 'mdi-view-dashboard', path: '/dashboard' },
          { title: 'Minha Conta', icon: 'mdi-account-box', path: '/account' },
          { title: 'Configurações', icon: 'mdi-cog', path: '/settings' },
          { title: 'Reservas', icon: 'mdi-calendar', path: '/reservations' },
        ];
      }
    }
  }
};
</script>