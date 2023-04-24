<template>
    <v-navigation-drawer app>
      <v-list dense>
        <v-list-item>
          <v-list-item-title>Login</v-list-item-title>
        </v-list-item>
        <v-list-item>
          <v-list-item-title>Register</v-list-item-title>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item>
          <v-list-item-title>Email</v-list-item-title>
          <v-text-field></v-text-field>
        </v-list-item>
        <v-list-item>
          <v-list-item-title>Password</v-list-item-title>
          <v-text-field type="password"></v-text-field>
        </v-list-item>
        <v-list-item>
          <v-list-item-title>Remember password</v-list-item-title>
          <v-checkbox></v-checkbox>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item>
          <v-list-item-title>About</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </template>
  
  <script>
  export default {
  };
  </script>
  
  <style>
  .v-navigation-drawer {
    background-color: #911010;
    color: white;
  }
  .v-list-item--active {
    background-color: #A16F6E;
  }
  .v-list-item__title {
    color: white;
  }
  </style>
  