<template>
  <div class="text-xs-center">
    <v-menu
      :close-on-content-click="false"
      :nudge-width="200"
      v-model="menu"
      offset-x
    >
      <!-- <v-btn slot="activator" color="indigo" dark>Profile</v-btn> -->
      <v-icon slot="activator">more_vert</v-icon>
      <v-card>
        <v-list>
          <v-list-tile avatar>
            <v-list-tile-avatar>
              <img :src="user.photoURL" alt="profile-photo" />
            </v-list-tile-avatar>
            <v-list-tile-content>
              <v-list-tile-title>{{user.displayName}}</v-list-tile-title>
              <v-list-tile-sub-title>{{user.email}}</v-list-tile-sub-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
        <v-divider></v-divider>
        <v-list>
          <v-list-tile>
            <v-list-tile-action>
              <v-btn
              class="ml-0 google-font hidden-sm-and-down"
              style="text-transform: capitalize;"
              flat
              @click="logout"
            >Logout</v-btn>
            </v-list-tile-action>
          </v-list-tile>
        </v-list>
      </v-card>
    </v-menu>
  </div>
</template>

<script>
export default {
  props: ["userData"],
  data() {
    return {
      user: {},
      menu: false,
    };
  },
  methods: {
    logout() {
      this.$emit("userLogout");
    }
  },
  mounted() {
    this.user = this.userData;
  }
};
</script>

<style>
</style>