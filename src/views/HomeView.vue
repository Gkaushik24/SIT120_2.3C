<template>
  <div>
    <h2>Cricket Match Details</h2>
    <p>Team A: {{ teamA }}</p> 
    <p>Team B: {{ teamB }}</p>
    <p v-html="matchDescription"></p> 


    <p :id="venueId"></p> 


    <p>Match Date: {{ matchDate }}</p> 


    <button @click="startMatch">Start Match</button> 


    <h2>Match Score</h2>
    <p>Total Runs: {{ totalRuns }}</p>
    <p>Total Wickets: {{ totalWickets }}</p>


    <h2>Player List</h2>
    <ul>
      <li v-for="player in players" :key="player.id">{{ player.name }}</li> 
    </ul>

    <button @click="recordWicket">Record Wicket</button> 
    <button @click="recordRunOut">Record Run Out</button> 

 
    <h2>Enter Match Details</h2>
    <label for="runs">Runs:</label>
    <input type="number" v-model="runs" /> 
    <br />
    <label for="wickets">Wickets:</label>
    <input type="number" v-model="wickets" /> 
    <label for="manOfTheMatch">Man of the Match:</label>
    <select v-model="manOfTheMatch">
      <option value="Virat Kohli">Virat Kohli</option>
      <option value="KL Rahul">Kl Rahul</option>
    </select> 
    <br />
    <label for="matchSummary">Match Summary:</label>
    <textarea v-model="matchSummary"></textarea> 

   
    <h2>Cricket Match Components</h2>
    <match-summary :summary="matchSummary"></match-summary> 
    <player-stats @wicket="handleWicketEvent"></player-stats> 
    <slot-example>

    </slot-example>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';


const teamA = ref('Team India');
const teamB = ref('Team Pakistan');
const matchDescription = '<p>Asia Cup 2023!</p>';
const venueId = 'cricket-stadium';
const matchDate = '2023-09-11';

const startMatch = () => {
  alert('Match has started!');
};


const totalRuns = ref(0);
const totalWickets = ref(0);

const players = ref([
  { id: 1, name: 'Virat Kohli' },
  { id: 2, name: 'Kl Rahul' },
  { id: 3, name: 'Kuldeep Yadav' },
]);


const recordWicket = () => {
  totalWickets.value++;
};

const recordRunOut = () => {
  totalWickets.value++;
};


const runs = ref(0);
const wickets = ref(0);
const manOfTheMatch = ref('');
const matchSummary = ref('');


const handleWicketEvent = (data) => {
  
};
</script>

<style>
.cricket-match {
  font-family: Arial, sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #1ecf1e;
  border: 1px solid #bb1f1f;
  box-shadow: 0 0 10px rgba(244, 236, 6, 0.1);
}

h2 {
  color: #12b140;
  margin-top: 10px;
}

p {
  margin: 5px 0;
}

button {
  background-color: #007bff;
  color: #e2bd29;
  border: none;
  padding: 10px 20px;
  margin-top: 10px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 5px 0;
}

label {
  display: block;
  margin-top: 10px;
  font-weight: bold;
}

input[type="number"],
select,
textarea {
  width: 100%;
  padding: 5px;
  margin: 5px 0;
  border: 1px solid #e3ff13;
  border-radius: 3px;
}

</style>
