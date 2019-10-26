<template>
  <v-content>
    <v-container class="fill-height" fluid>
      <v-row align="center" justify="center">
        <v-col sm="12" md="12" lg="11">
          <v-row>
            <v-col cols="6" lg="12" align="center" justify="center">
              <v-card class="mx-auto" color="#F9F9F9" max-width="400">
                <v-list-item two-line>
                  <v-list-item-content>
                    <v-list-item-title class="headline">Passenger</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>

                <v-card-text>
                  <v-text-field v-model="passenger.boarding_pass" label="Boarding Pass"></v-text-field>
                  <v-text-field v-model="passenger.car_number" label="Car Number"></v-text-field>
                </v-card-text>

                <v-divider></v-divider>

                <v-card-actions>
                  <v-btn class="mr-4" @click="passengerSave()">save</v-btn>
                </v-card-actions>
              </v-card>
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
  data: () => ({
    absolute: true,
    loading: false,
    snackbar: false,
    y: "top",
    x: null,
    mode: "",
    timeout: 6000,
    text: "Hello, I'm a snackbar",
    edit: false,
    dialog: false,
    dataUser: [],
    dataList: {},
    passenger: {
      boarding_pass: "",
      car_number: ""
    },
    passwordRules: [
      v => (v || "").length >= 8 || `Minimum Password charecter is 8`
    ],
    confirmPasswordRules: [
      v => (v || "").length >= 8 || `Minimum Password charecter is 8`,
      v => v == password.newPassword || "Should be same as new password"
    ]
  }),
  watch: {},
  created() {
    // console.log(this.dataList);
    // this.initialize();
  },
  methods: {
  
    async passengerSave() {
      try {
        let { data } = await axios({
          method: "post",
          url: "/app/save_passenger",
          data: this.passenger
        });
        this.passenger.boarding_pass="";
        this.passenger.car_number="";  
        	this.snacks("Success, Passenger Data Added", "green");      
      } catch (e) {
        this.loading = false;
        this.snacks("Operation Failed", "red");
      }
    },
   
  },
  
};
</script>

<style>
</style>