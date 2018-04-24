<template>

  <div>

    <form @submit.prevent="addAnimal">



  <label>Specie</label>
  <input v-model = "newAnimal.specie" type = "text"/>

  <label>Name</label>
  <input  v-model = "newAnimal.name" type = "text"/>

  <label>Date of birth</label>
  <input  v-model = "newAnimal.dateOfBirth" type = "number"/>

  <label>Sector</label>
  <input type="radio" v-model ="newAnimal.sector"  :value = "sectors[0]" checked> Wild animal<br>
  <input type="radio" v-model ="newAnimal.sector"  :value = "sectors[1]" > Domestic animal <br>

  <button type = "submit">Add Animal</button>
  
  <!-- {{newAnimal}} -->

  </form>




    <table style="width:50%" border="1px">
    <tr>
      <th>Species</th>
      <th>Name</th>
      <th>Year of birth</th>
      <th>Sector</th>


    </tr>

    <tr v-for= "(animal , key) in animals" :key = "key">
      <td>{{ animal.specie }}</td>
      <td>{{ animal.name }}</td>
      <td v-if = "animal.dateOfBirth != null">{{ animal.dateOfBirth }}</td>
      <td v-else >Unknown</td>
      <td>{{animal.sector.name}}</td>
      <td><button @click = "removeAnimal(animal)">Remove</button></td>
      <td><button @click = "moveToTop(animal)">Move to top</button></td>
    </tr>

      
    </table >


    <table style="width:50%" border="1px" >

      <tr>
      <th>Sector</th>
      </tr>

      <tr>

        <td>{{sectors[0].name}}</td>
        <td><button @click = "viewAnimals(sectors[0])">View all wild animals</button></td>

      </tr>

      <tr>
        <td>{{sectors[1].name}}</td>
        <td><button @click = "viewAnimals(sectors[1])" >View all domestic animals</button></td>
      </tr>
    </table>


  </div>

</template>

<script>


const sectors = [

      {name: 'Wild'},
      {name: 'Domestic'}


      ];

export default {

  name : 'AnimalsList',

  data() {

    return {
      sectors:sectors,
      animals: [
      { specie: 'Konj' , name: 'Kole' , dateOfBirth: 2015 , sector: sectors[1] },
      { specie: 'Krava' , name: 'Belka' , dateOfBirth: 2016, sector: sectors[1] },
      { specie: 'Svinja' , name: 'Gile' , dateOfBirth: 2018, sector: sectors[1] },
      { specie: 'Koza' , name: 'Angora' , dateOfBirth:  2017, sector: sectors[1] },
      { specie: 'Dzudzabajac' , name: 'Malaksijandar' , dateOfBirth: null, sector: sectors[0]  }

      ],

      newAnimal: {
        specie: '',
        name: '',
        yearOfBirth: '',
        sector: ''
      },


      







    }
  },

  methods: {

    removeAnimal(animal){

    this.animals.splice(this.animals.indexOf(animal),1)
    },

    moveToTop(animal){

      // var temp = animal;
      
      this.animals.splice(this.animals.indexOf(animal),1);
      this.animals.unshift(animal);

    },

    addAnimal() {
    this.animals.push(this.newAnimal)
    },

    viewAnimals(sectors){
      this.animals.forEach(function(animal) {
      if (sectors.name === animal.sector.name) { window.alert(animal.name)}
      });
    }
  }
}
  




</script>

<!-- vaka životinja treba da ima vrstu, ime i datum rođenja
 -->