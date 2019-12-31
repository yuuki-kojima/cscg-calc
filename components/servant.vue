<template>
  <v-col style="max-width: 150px">
    <v-card
      v-if="entity"
      class="mx-auto pa-2"
      :class="{
        'attacker': isAttacker,
        'magician': isMagician,
        'healer': isHealer,
        'defender': isDefender
      }"
      width="150"
      outlined
    >
      <p>{{ name }} ({{ resonance }})</p>
      order: {{ order }}<br>
      target: {{ target }}<br>
      range: {{ range }}
    </v-card>
    <v-card v-else class="mx-auto" height="130" outlined>
    </v-card>
  </v-col>
</template>

<script>
export default {
  name: 'Servant',
  props: [
    'servant'
  ],
  data() {
    return {
      entity: this.servant.entity,
      resonance: null,
      name: "",
      order: null,
      target: null,
      range: null,
      isAttacker: false,
      isMagician: false,
      isHealer: false,
      isDefender: false
    }
  },
  mounted() {
    if(this.entity) {
      this.resonance = this.servant.entity.resonance
      this.name = this.servant.entity.card.name
      this.order = this.servant.entity.card.speed
      this.target = this.servant.entity.card.target
      this.range = this.servant.entity.card.attack_range_pattern_id

      const jobValue = this.servant.entity.dna.job_value
      switch(jobValue) {
        case 0:
          this.isAttacker = true
          break;
        case 2:
          this.isMagician = true
          break;
        case 4:
          this.isHealer = true
          break;
        case 6:
          this.isDefender = true
          break;
        default:
          break;
      }
    }
  },
  watch: {
    servant: function(servant) {
      this.entity = servant.entity
      this.setParams(servant)
    }
  },
  methods: {
    setParams(servant) {
      this.isAttacker = false
      this.isMagician = false
      this.isHealer = false
      this.isDefender = false
      if(this.entity) {
        this.resonance = servant.entity.resonance
        this.name = servant.entity.card.name
        this.order = servant.entity.card.speed
        this.target = servant.entity.card.target
        this.range = servant.entity.card.attack_range_pattern_id

        const jobValue = servant.entity.dna.job_value
        switch(jobValue) {
          case 0:
            this.isAttacker = true
            break;
          case 2:
            this.isMagician = true
            break;
          case 4:
            this.isHealer = true
            break;
          case 6:
            this.isDefender = true
            break;
          default:
            break;
        }
      }
    }
  }
}



</script>

<style scoped>

.attacker p {
 color: red;
 font-weight: bold;
}

.magician p {
 color: fuchsia;
 font-weight: bold;
}

.healer p {
 color: lime;
 font-weight: bold;
}

.defender p {
 color: aqua;
 font-weight: bold;
}


</style>
