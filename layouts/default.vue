<template>
  <v-app dark>
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" :clipped="clipped" fixed app>
      <v-list>
        <v-list-tile v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"/>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar :clipped-left="clipped" fixed app>
      <v-toolbar-side-icon @click="drawer = !drawer"/>
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon>{{ `chevron_${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-btn icon @click.stop="clipped = !clipped">
        <v-icon>web</v-icon>
      </v-btn>
      <v-btn icon @click.stop="fixed = !fixed">
        <v-icon>remove</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title"/>
      <v-spacer/>
      <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>menu</v-icon>
      </v-btn>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt/>
      </v-container>
    </v-content>
    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-tile @click.native="right = !right">
          <v-list-tile-action>
            <v-icon light>compare_arrows</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <template>
      <v-footer dark height="auto">
        <v-card class="flex" flat tile>
          <v-card-title class="teal">
            <strong class="subheading">Get connected with us on social networks!</strong>

            <v-spacer></v-spacer>

            <v-btn v-for="icon in icons" :key="icon" class="mx-3" dark icon>
              <v-icon size="24px">{{ icon }}</v-icon>
            </v-btn>
          </v-card-title>

          <v-card-actions class="grey darken-3 justify-center">
            &copy;2018 —
            <strong>D-sides.</strong>
          </v-card-actions>
        </v-card>
      </v-footer>
    </template>
  </v-app>
</template>


<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "apps",
          title: "Welcome",
          to: "/"
        },
        {
          icon: "bubble_chart",
          title: "About",
          to: "/About"
        },
        {
          icon: "supervisor_account",
          title: "Member",
          to: "/Member"
        },
        {
          icon: "speaker_phone",
          title: "Access",
          to: "/Access"
        },
        {
          icon: "format_align_justify",
          title: "Form",
          to: "/Form"
        },
        {
          icon: "movie_filter",
          title: "Movie",
          to: "/Movie"
        },
        {
          icon: "directions_run",
          title: "Activity",
          to: "/Activity"
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "D-sides."
    };
  }
};
</script>
