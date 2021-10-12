<template>
  <v-app class="">
    <v-navigation-drawer permanent expand-on-hover app>
      <v-list>
        <v-list-item class="px-2">
          <v-list-item-avatar>
            <v-img></v-img>
          </v-list-item-avatar>
        </v-list-item>
      </v-list>
      <v-divider></v-divider>
      <v-list>
        <v-list-item link to="/">
          <v-icon>
            mdi-home
          </v-icon>
          <v-list-item-title>Home</v-list-item-title>
        </v-list-item>
        <v-list-item link to="/animation">
          <v-icon>
            mdi-transition
          </v-icon>
          <v-list-item-title>Animation</v-list-item-title>
        </v-list-item>
        <v-list-item link to="/bug">
          <v-icon>
            mdi-image
          </v-icon>
          <v-list-item-title>BUG</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      app
    >
      <div class="d-flex align-center">
        <v-img
          alt="xf Logo"
          contain
          :src="require('@/assets/logo.png')"
          width="100"
        />
      </div>
    </v-app-bar>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
