<template>
  <div>
    <h3>Formulaire satisfaction du service : </h3>
    <div v-for="q in questions" :key="q.id" class="mb-3">
      <h5>{{q.texte}}</h5>
      <Choice :question="q" @select="onSelect"/>
    </div>

    <b-button @click="valider" variant="primary">Valider</b-button>
    <hr>

    <div v-if="score != 0">
      Score: {{this.score}}<br>
      [0-30]: Mauvais<br>
      [30-50]: Mediocre<br>
      [50-60]: Correct<br>
      [60-80]: Bon<br>
      [80-100]: Excellent<br>
    </div>
  </div>
</template>

<script>
import Choice from '@/components/Choice.vue'

export default {
  name: 'Form',
  components: {
    Choice,
  },
  data(){
    return{
      score: 0,
      questions: [
        {id: "frequence", texte:"1. Je pense que vais utiliser le service fréquemment", consonnance: "positive"},
        {id: "complexite", texte:"2. Je pense que le service est inutilement complexe", consonnance: "negative"},
        {id: "facilite", texte:"3. Je pense que le service est facile d’utilisation", consonnance: "positive"},
        {id: "support", texte:"  4. Je pense que je vais devoir faire appel au support technique pour pouvoir utiliser ce service", consonnance: "negative"},
        {id: "integration", texte:"5. Je trouve que les fonctionnalités du service sont bien intégrées", consonnance: "positive"},
        {id: "incoherence", texte:"6. Je trouve qu’il y a beaucoup trop d’incohérences dans ce service", consonnance: "negative"},
        {id: "apprentissage", texte:"7. Je pense que la plupart des gens apprennent très rapidement à utiliser le service", consonnance: "positive"},
        {id: "lourdeur", texte:"8. Je trouve le service vraiment très lourd à utiliser", consonnance: "negative"},
        {id: "confiance", texte:"9. Je me suis senti très confiant en utilisant ce service", consonnance: "positive"},
        {id: "prerequis", texte:"10. J’ai dû apprendre beaucoup de choses avant de pouvoir utiliser ce service", consonnance: "negative"},
      ]
    }
  },
  methods:{
    valider(){
      //  console.log("quesions", this.questions)
      let tmp_score = 0

      this.questions.forEach((q) => {
        let valeur = q.result && q.result.score
        if (q.consonnance == "positive"){
          q.s =  valeur-1
        }else if(q.consonnance =="negative"){
          q.s =  5-valeur
        }
        //  console.log(q.s)
        tmp_score+= q.s
      });
      this.score = tmp_score * 2.5
      //  console.log("score : ",this.score )
      let resultat = {questions: this.questions, score: this.score}
      console.log("resultat",resultat)


      /*  Comment calculer le score SUS ?
      https://www.myfeelback.com/fr/blog/questionnaire-system-usability-scale-experience-client

      Le score SUS est compris entre 0 et 100. Mais attention, il ne s’agit pas d’un pourcentage. Le mode de calcul du SUS, standardisé, est le suivant :

      Pour les questions impaires, à consonnance positive, vous devez soustraire 1 au résultat donné par le répondant. Si le répondant répond 4, le score correspondant est 3 (4-1).

      Pour les questions paires à consonnance négative, le score est égal à 5 moins le score donné par le répondant. Si le répondant répond 3, le score est de 2 (5-3).

      Une fois le total calculé, vous devez le multiplier par 2,5. Vous obtenez ainsi le score SUS compris entre 0 et 100.

      Par exemple, pour avoir un score SUS de 100, il faut que le répondant réponde 5 à toutes les questions impaires et 0 à toutes les questions paires.
      */
    },
    onSelect(e){
      console.log(e.id, e)

    }

  }
}
</script>

<style>

</style>
