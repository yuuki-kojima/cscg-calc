<template>
  <v-content>
    <v-container fluid>
      <v-row
        align="center"
        justify="center"
      >
        <v-col md="6" sm="6" xs="12">
          <v-textarea
            v-model="enemyData"
            type="number"
            outlined
          ></v-textarea>
          <v-btn
            @click="calc()"
            color="success"
            dark
            block
          >
            <v-icon>submit</v-icon>
          </v-btn>
        </v-col>
      </v-row>
      <v-row
        v-if="opponents.length"
        align="center"
        justify="center"
      >
        <Opponent v-for="(opponent, index) in opponents" :key="index" :opponent="opponent" />
      </v-row>
    </v-container>
  </v-content>
</template>

<script>
import Opponent from "~/components/opponent"

export default {
  components: {
    Opponent
  },
  data() {
    return {
      enemyData: null,
      opponents: []
    }
  },
  created () {
    this.$vuetify.theme.dark = true
  },
  methods: {
    calc() {
      const json = JSON.parse(this.enemyData)
      this.opponents = json.opponents
      console.log(this.opponents)
    }
  }
}
</script>
