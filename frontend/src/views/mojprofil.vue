<template>
  <div class="mojprofil">
    <div class="info">
      <h3><strong>User information</strong></h3>
      <div class="okvir">
      <div class="roditelj">
      <div class="col-md-10">
          <div class="form-group row" >
            <label for="username" class="col-6"><strong>Ime</strong></label>
            <div class="col-6">
                {{user.ime}}
            </div>
          </div>
          <div class="form-group row">
            <label for="name" class="col-6"><strong>Prezime</strong></label>
            <div class="col-6">
                {{user.prezime}}
            </div>
          </div>
          <div class="form-group row">
            <label for="lastname" class="col-6"><strong>Država</strong></label>
            <div class="col-6">
              {{user.drzava}}
            </div>
          </div>
          <div class="form-group row">
            <label for="text" class="col-6"><strong>Grad</strong></label>
            <div class="col-6">
              {{user.grad}}
            </div>
          </div>
          <div class="form-group row">
            <label for="email" class="col-6"><strong>Koliko imam godina</strong></label> 
            <div class="col-6">
              {{user.godina}}
            </div>
          </div>
          <div v-if="user.tip== 'poslodavac' " class="form-group row">
            <label for="email" class="col-6"><strong>Kategorija posla</strong></label> 
            <div class="col-6">
              {{user.kategorija_posla}}
            </div>
          </div>
          <div v-if="user.tip== 'poslodavac' " class="form-group row">
            <label for="email" class="col-6"><strong>Opis posla</strong></label> 
            <div class="col-6">
              {{user.opis_posla}}
            </div>
          </div>
          <div v-if="user.tip== 'freelancer' " class="form-group row">
            <label for="email" class="col-6"><strong>Vještine</strong></label> 
            <div class="col-6">
              {{user.vjestine}}
            </div>
          </div>
          <div v-if="user.tip== 'freelancer' " class="form-group row">
            <label for="email" class="col-6"><strong>Minimalna zarada</strong></label> 
            <div class="col-6">
              {{user.minimalna_zarada}}
            </div>
          </div>
          <div v-if="user.tip== 'freelancer' " class="form-group row">
            <label for="email" class="col-6"><strong>Ostalo</strong></label> 
            <div class="col-6">
              {{user.ostalo}}
            </div>
          </div>
          <div class="form-group row">
            <label for="email" class="col-6"><strong>Email</strong></label> 
            <div class="col-6">
              {{user.email}}
            </div>
          </div>
      </div>
    </div>  
       <div style="width: 100%; text-align: right;" class="button"><a v-on:click="press"><button>Edit profile</button></a></div>
      </div>
    </div>
  </div>    
</template>


<script>
import {Auth} from '@/services';


export default {
  
   data() {
    return {
      user: {}
    };
  },
  methods: {
   profil(){
     this.user = Auth.profil()
   },
   press(){
     this.$router.push({path : `EditProfil/${this.user.email}`})
   }
  },
  created() {
        this.profil();
        
    },
}

</script>

<style scoped>
    button{
      width: 20%;
      padding: 1%;
    }
   .mojprofil{
    margin: 5%;
    min-height: 700px;   
  }

  .info{
    background-color:white;
    width: 60%;
    margin: auto;
    padding: 2% 0;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    box-shadow: 9px 9px 7px gray;
  }
  h3{
    text-align: left;
    margin: 1.5% 8%;
  }

  .okvir{
    border: rgb(233, 230, 230) 3px solid;
    width: 100%;
    padding: 3%;
    margin: auto;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
  }


</style>