<template>

  <div v-for="cand in candidatos">
    {{ cand.nome }}
  </div>



</template>

<script>
import axios from 'axios';

export default {
  name: "Main",
  data() {
    return {
      candidatos: []
    }
  },

  mounted() {
    this.buscarVotos();


  },

  methods: {
    buscarVotos() {
      axios.get('https://resultados.tse.jus.br/oficial/ele2022/544/dados-simplificados/br/br-c0001-e000544-r.json').then(result => {
        result.data.cand.forEach(pres => {
          this.candidatos.push({nome: pres.nm, perc: pres.pvap, seq: pres.seq});
        })




        console.log(result.data);
      })
    }
  }
/*cc: "PT - Federação Brasil da Esperança - FE BRASIL (PT/PC do B/PV) / SOLIDARIEDADE / Federação PSOL REDE (PSOL/REDE) / PSB / AGIR / AVANTE / PROS"
dvt: "Válido"
e: "s"
n: "13"
nm: "LULA"
nv: "GERALDO ALCKMIN"
pvap: "48,43"
seq: "1"
sqcand: "280001607829"
st: "2º turno"
vap: "57259504"*/



}

</script>

<style scoped>

</style>