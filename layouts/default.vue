<template>
  <v-app dark>
    <!-- desktop appbar -->
    <v-app-bar app color="black" class="hidden-xs-only" >
      <v-img
        alt="Vuetify Logo"
        class="shrink mr-2 img"
        contain
        src="https://ztf-shop.web.app/9.png"
        transition="scale-transition"
        width="40"
      />
      <v-app-bar-title>Qr on the GO !</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-btn icon href="https://github.com/ZTF666/QrCode-On-The-Go" target="_blank">
        <v-icon>mdi-github</v-icon>
      </v-btn>
    </v-app-bar>
    <!-- mobile appbar -->
<v-app-bar :clipped-left="clipped" fixed app color="black" class="hidden-sm-and-up">
     <v-img
        alt="Vuetify Logo"
        class="shrink mr-2 img"
        contain
        src="https://ztf-shop.web.app/9.png"
        transition="scale-transition"
        width="40"
      />
     <v-app-bar-title>Qr on the GO !</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-menu left bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <!-- <v-list-item> -->
          <v-list-item-content>
            <!-- <v-spacer></v-spacer> -->
          <v-btn icon href="https://github.com/ZTF666/QrCode-On-The-Go" target="_blank"> <v-icon>mdi-github</v-icon> </v-btn>

        </v-list-item-content>

          <!-- </v-list-item> -->
        </v-list>
      </v-menu>
    </v-app-bar>
    <!--  -->

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  
    <v-footer color="black" app >
      <center><span>&copy; {{ new Date().getFullYear() }}</span></center>
       <v-spacer></v-spacer>
      <span>
        Made with ❤️ by
        <a
          href="https://ztfportfolio.web.app/"
          target="blank"
          class="purple--text "
        >
          <strong>ZTF</strong>
        </a>
      </span>
    </v-footer>
  </v-app>
</template>

<script>

export default {

  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
