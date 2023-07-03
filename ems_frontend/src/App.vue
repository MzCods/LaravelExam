<template>
  <div>
    <div class="hidden" v-if="isLogged && loggedInUserEmail === 'mz@gmail.com'">
      <vs-sidebar class="sidebar" hover-expand reduce v-model="active" open>
        <template #logo>
          <img
            src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Logo_EMS.svg/1280px-Logo_EMS.svg.png"
          />
        </template>
        <!-- :::::::::::::::::::::: -->
        <!-- SideMenu Item List Goes here -->
        <!-- :::::::::::::::::::::: -->
        <vs-sidebar-item
          id="newevent"
          to="/newevent"
          v-if="isLogged "
          class="newevent"
        >
          <template #icon>
            <box-icon name="plus"></box-icon>
          </template>
          Nouvel évènement
        </vs-sidebar-item>
        <vs-sidebar-item id="dashboard" to="/Dashboard" v-if="isLogged ">
          <template #icon>
            <box-icon name="home-smile"></box-icon>
          </template>
          Tableau de bord
        </vs-sidebar-item>
        <vs-sidebar-item id="reports" to="/reports" v-if="isLogged ">
          <template #icon>
            <box-icon name="stats"></box-icon>
          </template>
          Rapports
        </vs-sidebar-item>
      </vs-sidebar>
    </div>

    <div id="nav" class="center examplex">
      <vs-navbar center-collapsed fixed shadow>
        <h4>SYSTÈME DE GESTION DES ÉVÉNEMENTS</h4>
        <img
          src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Logo_EMS.svg/1280px-Logo_EMS.svg.png"
          class="app-logo-header"
        />

        <template #right>
          <vs-button flat to="/login" v-if="!isLogged">Connexion</vs-button>
          <vs-chip v-if="isLogged" class="login-user-chip">
            <span class="login-user-label">{{ loggedInUserEmail }}</span>
            <vs-button @click="logout()"> Se déconnecter</vs-button>
          </vs-chip>
        </template>
      </vs-navbar>
    </div>
    <router-view />
    <div class="footer">
      Copyright © 2022 https://github.com/ch-hassansaeed
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
  computed: {
    ...mapGetters(['isLogged']),
    isDashboardUserRoute() {
      // Vérifiez si la route active correspond à "/dashboardUser"
      return this.$route.path === '/DashboardUser';
    },
  },
  data() {
    return {
      active: 'dashboard',
      loggedInUserEmail: '',
    };
  },

  methods: {
    logout() {
      this.$store.dispatch('logout');
    },
  },
  watch: {
    isLogged: {
      handler() {
        //on update isLogged get the user email from localStorage
        const loggedInUser = JSON.parse(localStorage.getItem('user'));
        const loggedInUserEmailVal = loggedInUser ? loggedInUser.email : '';
        console.log(loggedInUserEmailVal);
        this.loggedInUserEmail = loggedInUserEmailVal;
      },
      deep: true,
    },
  },
};
</script>

<style src="@/assets/css/style.css" />
