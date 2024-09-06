<template>
  <v-responsive class="border rounded" >
      <v-app>
          <v-app-bar :elevation="2" style="background-color: #694F8E;">
              <template v-slot:prepend>
              </template>

                  <v-btn prepend-icon="mdi-check-circle" @click="logout">
                      <template v-slot:prepend>
                          <v-icon color="success"></v-icon>
                      </template>
                      Logout
                  </v-btn>
          </v-app-bar>



          <v-main style="background-color: #F5EDED; ">
              <v-container>
                  <v-carousel>
                      <v-carousel-item src="https://a-static.besthdwallpaper.com/astronaut-playing-games-wallpaper-2880x1620-84511_52.jpg" cover></v-carousel-item>

                      <v-carousel-item src="https://wallpapers.com/images/featured/4k-space-9w27dqmc4nrs3xwd.jpg" cover></v-carousel-item>

                      <v-carousel-item src="https://hdwallpaperim.com/wp-content/uploads/2017/08/22/433385-astronaut-ultra-wide-space-space_art-science_fiction-748x316.jpg"
                          cover></v-carousel-item>
                  </v-carousel>
                  <h1>Main Content</h1> <v-row>
                      <v-col v-for="n in 9" :key="n" class="d-flex child-flex" cols="4">
                          <v-img :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
                              :src="`https://picsum.photos/500/300?image=${n * 5 + 10}`" aspect-ratio="1"
                              class="bg-grey-lighten-2" cover>
                              <template v-slot:placeholder>
                                  <v-row align="center" class="fill-height ma-0" justify="center">
                                      <v-progress-circular color="grey-lighten-5" indeterminate></v-progress-circular>
                                  </v-row>
                              </template>
                          </v-img>
                      </v-col>
                  </v-row>
              </v-container>
          </v-main>
      </v-app>
  </v-responsive>


  
</template>

<script>
import axios from "axios";
export default {
data: () => ({
    id: '',
    username: '',
    email: '',
    status: '',
    passwd: '',
    picture: '',
}),
async mounted() {
  let user = window.sessionStorage.getItem("email");
  console.log("user=", user);
 const response = await axios.get("http://localhost:7000/listid?email="+ user);
 let data = response.data;
 console.log('user=',data.row.username)
 this.email=data.row.email
 this.username=data.row.username
},
methods: {
  logout() {
    window.sessionStorage.clear();
    this.$router.replace("/login");
  },
},
};
</script>