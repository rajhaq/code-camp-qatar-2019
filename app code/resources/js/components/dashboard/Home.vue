<template>
  <v-content>
    <v-container class="fill-height" fluid>
      <v-row align="center" justify="center">
       <v-col sm="12" md="12" lg="11">
        <v-row >
        <v-col cols="6"  lg="12" align="center" justify="center"> 
        <v-text-field
        flat
        solo-inverted
        hide-details
        prepend-inner-icon="search"
        label="Boarding Pass"
        class="hidden-sm-and-down"
      ></v-text-field>
        </v-col>
        </v-row>
        <v-row >
        <v-col cols="12"  lg="12" align="center" justify="center">  
        <v-btn class="mx-2" x-large fab dark color="indigo" >
        <v-text>Go</v-text>
    </v-btn>
        </v-col>
        </v-row>
         </v-col>
        <!-- <v-row>
       <v-col sm="12" md="12" lg="11">
        <v-row>
        <v-col sm="12" md="12" lg="11">
        <v-btn class="mx-2" fab dark color="indigo">
      <v-icon dark>mdi-plus</v-icon>
    </v-btn>
       </v-col>
        </v-row>
         </v-col>-->
      
      </v-row> 
    </v-container>
  </v-content>
</template>

<script>
export default {
  props: {
    source: String
  },
  data: () => ({}),
  components: {}
};
</script>