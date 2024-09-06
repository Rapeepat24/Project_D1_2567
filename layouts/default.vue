<template>
  <v-app>
    <v-card>
      <v-layout>
      
        <v-app-bar
          color="teal-darken-4"
          image="https://wallpapers.com/images/hd/banner-background-b5a2ptzqzslvvuvv.jpg">
          <v-app-bar-title>My account</v-app-bar-title>
        </v-app-bar>

        <v-navigation-drawer 
          class="bg-black"
          v-model="drawer"
          :rail="rail"
          permanent
          @click="rail = false"
        >
        
          <v-list-item

            title="My Profile"
            nav
          >
          
            <template v-slot:append>
              <v-btn
                icon="mdi-chevron-left"
                variant="text"
                @click.stop="rail = !rail"
              ></v-btn>
            </template>
          </v-list-item>
          <v-divider></v-divider>
          <v-list density="compact" nav>
            <v-list-item
              prepend-icon="mdi-home-city"
              title="หน้าหลัก"
              value="home"
              @click="main"
            ></v-list-item>
            <v-list-item
           
              prepend-icon="mdi-plus"
              size="x-large"
              title="เพิ่มข้อมูล"
              value="add"
              @click="add"
            ></v-list-item>
            <v-list-item
              prepend-icon="mdi-home-city"
              title="แสดงข้อมูล"
              value="home"
              @click="showdata"
            ></v-list-item>
            <v-list-item
              prepend-icon="mdi-account"
              title="เกี่ยวกับ"
              value="account"
              @click="about"
            ></v-list-item>
            <v-list-item
              prepend-icon="mdi-close-circle"
              title="LOGOUT"
              value="users"
              @click="logOut"
            ></v-list-item>
          </v-list>
        </v-navigation-drawer>
        <!-- <v-main style="height: 650px"></v-main> -->
        <v-main >
         <NuxtPage></NuxtPage>
          <!-- Main Content -->
        </v-main>
        <!--  -->
      </v-layout>
    </v-card>
  </v-app>
</template>
<script>
import axios from 'axios';
export default {
  data() {
    return {
      drawer: true,
      rail: true,
      username: '',
      email: '',
    };
  },
  async mounted() {
    let user = window.sessionStorage.getItem("email");
    console.log("user=", user);
    if (!user) {
      this.$router.replace("/login");
      return
    }
  },
  methods: {
    main(){
      this.$router.replace("/home");
    },
    listdata(){
      this.$router.replace("/listdata");
    },
    showdata(){
      this.$router.replace("/showdata");
    },
    about(){
      this.$router.replace("/app_mqtt");
    },
    add(){
      this.$router.replace("/add");
    },
    logOut() {
      window.sessionStorage.clear();
      this.$router.replace("/login");
    },
  },
};
</script>

