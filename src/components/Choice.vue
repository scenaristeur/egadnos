<template>
  <b-row>
    <b-col md
    v-for="l in likert" :key="l.id">
    <b-button
    class="button"
    :pressed.sync="l.state"
    variant="outline-secondary"
    @click="select(l)"

    >{{l.texte}}</b-button>
  </b-col>
</b-row>
</template>

<script>
export default {
  name:'Choice',
  props: ['question'],
  created(){
    this.q = this.question
  this.q.result = this.likert[2] //initialisation du resultat au neutre
  },
  data(){
    return{
      likert: [
        {id:1, texte: "Pas du tout d'accord", state: false, score: 1},
        {id:2, texte: "Pas d'accord", state: false, score: 2},
        {id:3, texte: "Ni d'accord, ni pas d'accord", state: true, score: 3},
        {id:4, texte: "D'accord", state: false, score: 4},
        {id:5, texte: "Tout à fait d'accord", state: false, score: 5},
      ]
    }
  },
  methods:{
    select(s){
      console.log(s)
      this.likert.forEach(l =>{
        //  console.log(l.id)
        l.id == s.id ? l.state = true : l.state = false
      })
      this.q.result = s
      this.$emit('select', this.q)
    }
  }
}
</script>

<style>

</style>
