<template>
  <v-content>
    <v-container class="fill-height" fluid>
      <v-row align="center" justify="center">
        <v-col sm="12" md="12" lg="11">
          <v-row>
            <v-col cols="6" lg="12" align="center" justify="center">
              <template>
                <v-card max-width="500" class="mx-auto">
                  <v-toolbar color="indigo" dark>
                    <v-app-bar-nav-icon></v-app-bar-nav-icon>

                    <v-spacer></v-spacer>

                    <v-btn icon>
                      <v-icon>mdi-magnify</v-icon>
                    </v-btn>

                    <v-btn icon>
                      <v-icon>mdi-dots-vertical</v-icon>
                    </v-btn>
                  </v-toolbar>
                  <v-list>
                    <v-list-item >
                      <v-list-item-icon>
                       <v-list-item-title >Name:</v-list-item-title>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title v-text="driver.name"></v-list-item-title>
                      </v-list-item-content>

                       <v-list-item-avatar>
          <v-img :src="pic.avatar"></v-img>
        </v-list-item-avatar>
                    </v-list-item>
                    <v-list-item >
                      <v-list-item-icon>
                       <v-list-item-title >Email :</v-list-item-title>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title v-text="driver.email"></v-list-item-title>
                      </v-list-item-content>

                      <v-list-item-avatar>
                        <v-img ></v-img>
                      </v-list-item-avatar>
                    </v-list-item>
                    <v-list-item >
                      <v-list-item-icon>
                       <v-list-item-title > Car No:</v-list-item-title>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title v-text="driver.car_number"></v-list-item-title>
                      </v-list-item-content>

                      <v-list-item-avatar>
                        <v-img ></v-img>
                      </v-list-item-avatar>
                    </v-list-item>
                  </v-list>
                </v-card>
              </template>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </v-content>
</template>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      <v-snackbar
        v-model="snackbar"
        :vertical="snackvertical"
        :timeout="snacktimeout"
        :top="snacktop"
        :color="snackcolor"
      >
        {{ snacktext }}
        <v-btn color="white" text @click="snackbar = false">Close</v-btn>
      </v-snackbar>
    </v-container>
  </v-content>
</template>
<script>
export default {
  data() {
    return {
      driver: {
        name: "",
        email: "",
        car_number: ""
      },
      pic: 
        {
          icon: true,
         
          avatar: "https://cdn.vuetifyjs.com/images/lists/1.jpg"
        },
        
    };
  },
  created() {
    console.log(this.initialize);
    this.initialize();
  },
  methods: {
    async initialize() {
      try {
        let { data } = await axios({
          method: "get",
          url: "/app/save_passenger"
        });
        this.driver = data;
      } catch (e) {
        this.snacks("Failed, company loading", "red");
      }
    }
  }
};
</script>