<template>
    <v-app>
      <v-app-bar color="red" class="flex-grow-0" app light>
        <v-app-bar-title></v-app-bar-title>
      </v-app-bar>
      <template v-if="!authenticated">
          <LoginComponent />
      </template>
      <v-navigation-drawer app permanent v-if="authenticated">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="text-h6"> SACCE </v-list-item-title>
            <v-list-item-subtitle> UFPE </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
        <v-list dense nav>
          <v-list-item v-for="item in items" :key="item.title" link>
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
  export default {
    name: 'App',
    data: () => ({
      items: [
        { title: 'Dashboard', icon: 'mdi-view-dashboard' },
        { title: 'Account', icon: 'mdi-account-box' },
        { title: 'Settings', icon: 'mdi-cog' },
      ],
    }),
  };
  </script>