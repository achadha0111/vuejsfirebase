<template>
  <div id="app" class="container">
    <div class="page-header">
    <h1> Browse Internships at WorkTeen</h1>
    </div>
    <div class="row">
    <!-- <div class="input-field col s12">
      <input placeholder="Search for internships" id="title" type="text" class="validate">
    </div>
    <div class="input-field col s12">
      <a class="waves-effect waves-light btn">Search</a>
    </div>
    -->
    <div v-on:submit.prevent="addpos">
    <h4> Add internships </h4>
        <div class="input-field col s6">
          <input id="title" type="text" class="validate" v-model="newpos.title">
          <label for="title">Opportunity Title</label>
        </div>
        <div class="input-field col s6">
          <input id="organisation" type="text" class="validate" v-model="newpos.organisation">
          <label for="organisation">Organisation</label>
        </div>
        <div class="input-field col s3">
          <input id="duration" type="text" class="validate" v-model="newpos.duration">
          <label for="duration">Duration</label>
        </div>
        <div class="input-field col s3">
          <input id="apply-by" type="text" class="validate" v-model="newpos.applyby">
          <label for="apply-by">Apply By</label>
        </div>
        <div class="input-field col s3">
          <input id="stipend" type="text" class="validate" v-model="newpos.stipend">
          <label for="stipend">Stipend</label>
        </div>
        <div class="input-field col s3">
          <input id="details-url" type="text" class="validate" v-model="newpos.url">
          <label for="details-url">URL for More Details</label>
        </div>
      </div>
      <div class="col s12">
      <a class="waves-effect waves-light btn" type="submit">Add Internships</a>
      </div>
    </div>
    <div class="row results-row">
  <div  v-for="pos in positions" class="col s12 m4">
    <div class="card">
      <div class="card-image">
        <img src="https://static.pexels.com/photos/7075/people-office-group-team.jpg">
        <span class="card-title">{{pos.title}} at {{pos.organisation}}</span>
      </div>
      <div class="card-content">
        <p>Stipend: {{pos.stipend}}</p>
        <p>Duration: {{pos.duration}}</p>
        <p>Apply By: {{pos.apply_by}}</p>
      </div>
      <div class="card-action">
        <a v-bind:href="pos.details_url" >Apply Now</a>
      </div>
    </div>
  </div>
</div
  </div>
  </div>

</template>

<script>
import Hello from './components/Hello'
import Firebase from 'firebase'

let config = {
   apiKey: "AIzaSyCCN3USnjztk1GcnrHVScsyRvedRdpI7YQ",
   authDomain: "vue-trial-1.firebaseapp.com",
   databaseURL: "https://vue-trial-1.firebaseio.com",
   projectId: "vue-trial-1",
   storageBucket: "vue-trial-1.appspot.com",
   messagingSenderId: "136352030230"
}

let app = Firebase.initializeApp(config);
let db = app.database();

let posRef = db.ref('opportunities');



export default {
  name: 'app',
  firebase: {
  positions: posRef
  },

  data() {
  return {
    newpos: {
    title: '',
    organisation: '',
    stipend: '',
    duration: '',
    applyby: '',
    url: ''
    }
  }
  },
  methods: {
    addpos: function() {
      posRef.push(this.newpos)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Lato', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.card-title{
font-size:10px;
text-align: left;
}
.card-content{
text-align:left;
}

.results-row{
margin-top:3%;
}
</style>
