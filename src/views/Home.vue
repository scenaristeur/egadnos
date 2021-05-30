<template>
  <div class="home">

    <b-container class="form-container">
      <Form v-if="service!= null" :service="service"/>

      <HelloWorld msg="Bienvenu.e sur Egadnos, le sondage ethique"/>
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Form from '@/components/Form.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    Form
  },
  data(){
    return{
      service: null
    }
  },
  async created(){
    this.checkQuery()
  },
  watch:{
    $route (){
      this.checkQuery()
    },
  },
  methods:{
    checkQuery(){
      if(this.$route.query.service){
        try{
          this.service = JSON.parse(decodeURIComponent(this.$route.query.service))
          console.log(this.service)
        }catch(e){
          console.log(e,"service inexploitable", this.$route.query.service)
        }
      }
    },
  }
}
</script>
<style>
.home{
  text-align: left;
}
</style>
