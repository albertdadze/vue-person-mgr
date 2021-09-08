<template>
 <div class="container">
    <Header @add-person="onAddPerson" title="Person Tracker" color="red" /> 
    <Persons
       :persons="persons"
       @delete-person="onDeletePerson"
       @toggle-person="onTogglePerson" />
 </div>
</template>

<script>
import { defineComponent } from 'vue';
import Header from './components/Header.vue';
import Persons from './components/Persons.vue';

export default defineComponent({
  name: 'App',
  components: { 
    Header, Persons,
  }, 
  data() {
    return {
      persons: [],
    }
  },
  methods: {
      onAddPerson({ person }){
        //console.log(person);
        //this.persons = [...this.persons, person]
        this.persons.unshift(person);
      },
      onDeletePerson(id){
        if(confirm('Are you sure you want to delete person?')){
         this.persons = this.persons.filter((person) => person.id !== id)
        }
      },
      onTogglePerson(id){
        //console.log(id);
        this.persons = this.persons.map((person) => 
          person.id === id ? {...person, selected: !person.selected} : person);
      }
  }, 
  created(){
    this.persons = []
  }
});


</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
  @import url('https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.1.0/css/bootstrap.min.css');

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: 'Poppins', sans-serif;
  }

  .container {
    max-width: 700px;
    margin: 30px auto;
    overflow: auto;
    min-height: 200px;
    border: 1px solid firebrick;
    padding: 30px;
    border-radius: 5px;
  }

  .btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
  }

  .btn:focus {
    outline: none;
  }

  .btn:active {
    transform: scale(0.98);
  }

  .btn-block {
    display: block;
    width: 100%;
  }

  [v-cloak]{
    display: none;
  }
</style>

