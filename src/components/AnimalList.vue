<template>

  <div>
    <table style="width:80%" border="1px">
    <tr>
      <th>Species</th>
      <th>Name</th>
      <th>Year of birth</th>
    </tr>

    <tr v-for= "(animal , key) in animals" :key = "key">
      <td>{{ animal.specie }}</td>
      <td>{{ animal.name }}</td>
      <td>{{ animal.dateOfBirth }}</td>
    </tr>
      
    </table>
  </div>

</template>

<script>

export default {

  name : 'AnimalsList',

  data() {

    return {
      animals: [
      { specie: 'Konj' , name: 'Kole' , dateOfBirth: '2015' },
      { specie: 'Krava' , name: 'Belka' , dateOfBirth: '2016' },
      { specie: 'Svinja' , name: 'Gile' , dateOfBirth: '2018' },
      { specie: 'Koza' , name: 'Angora' , dateOfBirth:  '2017 '},
      { specie: 'Dzudzabajac' , name: 'Malaksijandar' , dateOfBirth: '956' }

      ]
    }
  }
}
  




</script>

<!-- vaka životinja treba da ima vrstu, ime i datum rođenja
 -->