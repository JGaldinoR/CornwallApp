<template>
<v-app id="inspire" dark>
    <v-navigation-drawer
      clipped
      fixed
      v-model="drawer"
      app
    >
      <v-list dense>
        <v-list-tile @click="">
          <v-list-tile-action>
            <v-icon>dashboard</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Dashboard</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="">
          <v-list-tile-action>
            <v-icon>settings</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>Settings</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar app fixed clipped-left>
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title>Cornwall</v-toolbar-title>
    </v-toolbar>
     </v-toolbar>
    <v-content>
      <cornwall-daily/>
    </v-content>
    <v-footer :fixed="fixed" app>
      <span>&copy; Riki rikin enterprise 2018</span>
    </v-footer>
    </v-app>
</template>

<script>
import CornwallDaily from './components/CornwallDaily'

export default {
  name: 'App',
  components: {
    CornwallDaily
  },
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [{
        title: 'Riki'
      }],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Cornwall Daily Status Meeting'
    }
  }
}
</script>


