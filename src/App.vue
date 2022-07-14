<template>
  <v-app id="inspire">

    <v-navigation-drawer 
      v-model="drawer"
      app
      light
      class="pt-2"
      src="../public/hd-green-wallpaper.jpg"
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h4 text--white">
            To-Do list
          </v-list-item-title>
          <v-list-item-subtitle class="text--white">
            Vue & Vuetify
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        large
        nav
        rounded
        flat
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to" 
          link
        >
          <v-list-item-icon>
            <v-icon large>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title class="caption text-decoration-underline text-h6">{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar 
    app 
    color="green"
    src="../public/hd-green-wallpaper.jpg"
    dark
    elevate-on-scroll
    height="80"
    >
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-img
        lazy-src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/langfr-220px-Vue.js_Logo_2.svg.png"
        contain
        max-height="50"
        max-width="50"
        src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/langfr-220px-Vue.js_Logo_2.svg.png"
        class="mr-3"
      ></v-img>
      <v-toolbar-title class="text--green">Application VuetiFy</v-toolbar-title>
      
    </v-app-bar>

    <v-main>
      <router-view><!-- Component content --></router-view>
    </v-main>
  </v-app>
</template>



<script>
  export default {
    data: () => ({ 
      drawer: null,
      items: [
          { title: 'To-Do', icon: 'mdi-format-list-checks', to:'/' },
          { title: 'Photos', icon: 'mdi-image', to: '/photos' },
          { title: 'A propos', icon: 'mdi-help-box', to:'/about' },
        ],
      right: null, 
    }),
  }
</script>