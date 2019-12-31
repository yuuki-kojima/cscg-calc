<template>
  <v-content>
    <v-container>
      <v-row
        align="center"
        justify="center"
      >
        <v-col class="shrink" md="2" sm="4" xs="12">
          <v-card
            class="mx-auto"
            block
          >
            <v-img
              class="white--text align-end"
              src="/cscg_diana.jpeg"
            >
            </v-img>
            <v-text-field
              v-model="parentATokenId"
              type="number"
              placeholder="Enter Token ID"
              outlined
              dense
              clearable
              hide-details
            ></v-text-field>
          </v-card>
        </v-col>
        <v-col class="shrink" md="2" sm="4" xs="12">
          <v-card
            class="mx-auto"
            block
          >
            <v-img
              class="white--text align-end"
              src="/cscg_diana.jpeg"
            >
            </v-img>
            <v-text-field
              v-model="parentBTokenId"
              type="number"
              placeholder="Enter Token ID"
              outlined
              dense
              clearable
              hide-details
            ></v-text-field>
          </v-card>
        </v-col>
      </v-row>
      <v-row
        align="center"
        justify="center"
      >
        <v-col class="shrink" md="4" sm="8" xs="12">
          <v-btn
            @click="mix()"
            color="success"
            x-large
            dark
            block
          >
            <v-icon>MIX</v-icon>
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-content>
</template>

<script>
  export default {
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
      parentATokenId: "",
      parentBTokenId: ""
    }),
    created () {
      this.$vuetify.theme.dark = true
    },
    methods: {
      mix() {
        console.log(this.parentATokenId)
      }
    }
  }
</script>
