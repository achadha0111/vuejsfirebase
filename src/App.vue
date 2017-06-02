<template>
  <div id="app" class="container">
    <div class="row">
    <!-- <div class="input-field col s12">
      <input placeholder="Search for internships" id="title" type="text" class="validate">
    </div>
    <div class="input-field col s12">
      <a class="waves-effect waves-light btn">Search</a>
    </div>
    -->

    <div class="row results-row">
      <h4> Featured Opportunities </h4>
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
  }
}
</script>

<style>
body{
  font-family: 'Lato', Helvetica, Arial, sans-serif;
}
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

.title{
  font-family: 'Lato';
  text-align: center;
  font-size: 4em;
  color: white;
  margin-top:20px;
}

.intro{
  background-image: url('index-bg.jpeg');
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: center;
  padding:18%;
  margin-top: -20px;
}

.page-footer{
  background-image: url('index-bg.jpeg');
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: center;
}

#search{
  text-align: center;
  color: white;
  font-size: 20px;
  border-bottom: 1px solid white;
}
.search-panel{
  text-align: center;
}

.search-btn{
  width:30%;
  background-color: transparent;
  border: 1px white solid;
}

.search-btn:hover{
  background-color: rgba(0,0,0,0.4)
}

#search:active{
  border-bottom: 1px solid white;
}
</style>
