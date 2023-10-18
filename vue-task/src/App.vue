<template>
  <div id="app" class="container">
    <HeaderComponent :isLoggedIn="isLoggedIn" @login="login" @logout="logout" />
    <div v-if="isLoggedIn" class="content">
      <div class="navigation-column">
        <NavigationComponent @change-tab="changeTab" />
      </div>
      <div class="main-column">
        <router-view :user="user" />
      </div>
    </div>
  </div>
</template>

<script>
import HeaderComponent from "@/components/HeaderComponent.vue";
import NavigationComponent from "@/components/NavigationComponent.vue";

export default {
  components: {
    HeaderComponent,
    NavigationComponent
  },
  data() {
    return {
      isLoggedIn: false,
      user: {
        name: "Karlis",
        surname: "Barons",
        code: "IT-21074"
      }
    };
  },
  methods: {
    login() {
      this.isLoggedIn = true;
    },
    logout() {
      this.isLoggedIn = false;
    },
    changeTab(tab) {
      if (tab === "HOME") {
        this.$router.push({ path: "/" });
      } else if (tab === "ABOUT ME") {
        this.$router.push({ path: "/about" });
      }
    }
  }
};
</script>
<style>
.container {
  display: flex;
  flex-direction: column;
  height: 100vh;
}
.content {
  display: flex;
  flex: 1;
}
.navigation-column {
  flex: 0 0 200px;
  background-color: #f1f1f1;
  padding: 20px;
}
.main-column {
  flex: 1;
  padding: 20px; 
  background-color: #ffffff; 
}
.app {
  background-color: darkblue;
}

</style>
