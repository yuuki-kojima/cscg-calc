<template>
  <v-col md="4" sm="4" xs="4">
    <v-card class="mx-auto px-2" outlined>
      <v-row align="center" justify="center">
        ID:{{ userId }} NAME: {{ userName }}
      </v-row>
      <v-row align="center" justify="start" style="flex-direction: column; height: 900px">
        <Servant v-for="(servant, index) in deck" :key="index" :servant="servant"/>
      </v-row>
    </v-card>
  </v-col>
</template>

<script>
import Servant from "~/components/servant"

export default {
  name: 'Opponent',
  components: {
    Servant
  },
  props: [
    'opponent'
  ],
  data() {
    return {
      userId: this.opponent.opponent_user_id,
      userName: this.opponent.user_name,
      deck: this.opponent.deck
    }
  },
  watch: {
    opponent: function(opponent) {
      this.userId = opponent.opponent_user_id
      this.userName = opponent.user_name
      this.deck = opponent.deck
    }
  }
}
</script>
