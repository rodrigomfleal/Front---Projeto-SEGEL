<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>SACCE</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text :to="{ path: '/logout' }">Logout</v-btn>
    </v-app-bar>

    <v-navigation-drawer app permanent v-model="drawer" color="primary" dark>
      <v-list>
        <v-list-item
          v-for="(item, index) in menuItems"
          :key="index"
          link
          :to="item.path"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <v-container fluid>
        <slot></slot>
      </v-container>
    </v-content>

    <v-footer app>
      <span>&copy; 2023 SACCE - SEGEL UFPE</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'menuLayout',
  data() {
    return {
      drawer: false,
      menuItems: [
        { title: 'Dashboard', icon: 'mdi-view-dashboard', path: '/dashboard' },
        { title: 'Minha Conta', icon: 'mdi-account-box', path: '/account' },
        { title: 'Configurações', icon: 'mdi-cog', path: '/settings' },
        { title: 'Reservas', icon: 'mdi-calendar', path: '/reservations' },
      ],
    };
  },
};
</script>
