<template>
  <div>

    <h4>add another animal to our zoo</h4>

    <form @submit.prevent="addAnimal">

      <label>Add animal type</label>
      <input v-model="newAnimal.type"  type="text" placeholder="animal type"/>


      <label>Add animal name</label>
      <input v-model="newAnimal.name" type="text" placeholder="animal name"/>


      <label>Add animal date of birth</label>
      <input type="text" v-model="newAnimal.dateOfBirth" placeholder="date of birth"/>


              <button type="submit">add animal</button>

    </form>


    <h3>List of animals in the local zoo</h3>

    <table>

      <thead>
      <th>Animal Type</th>
      <th>Name</th>
      <th>date of birth</th>
      <th>remove from the list</th>
      <th>option</th>

      </thead>

      <tbody>
      <tr v-for="(animal,key) in animals" :key="key">

        <td>{{ animal.type }}</td>
        <td>{{ animal.name }}</td>

        <td v-if="animal.dateOfBirth != ''">{{ animal.dateOfBirth }}</td>
        <td v-else> Nepoznat </td>
        <td><button @click="removeAnimal(animal)">remove </button></td>
        <td><button @click="moveToTop(key)">move to the top</button></td>

      </tr>

      </tbody>



    </table>

  </div>
</template>

<script>
export default {
  name: 'AnimalList',
 data(){

      return{
          animals:[

              {
                  type: 'reptile',
                  name: 'Sima the Lizard',
                  dateOfBirth: '25.02.1988'
              },

              {
                  type: 'insect',
                  name: 'Pera the Fly',
                  dateOfBirth: '25.05.1955'
              },

              {
                  type: 'sponge',
                  name: 'SpongeBob',
                  dateOfBirth: '25.02.1980'
              },

              {
                  type: 'amphibious ',
                  name: 'John the Frog',
                  dateOfBirth: '25.02.1988'
              },

              {
                  type: 'mammals',
                  name: 'Timmy the Bear',
                  dateOfBirth: '25.08.2005'
              },

              {
                  type: 'mammals',
                  name: 'Timmy the Lion',
                  dateOfBirth: '',
              },


          ],

          newAnimal:{

              type: '',
              name: '',
              dateOfBirth: '',
          }




      }


 },

 methods: {

     removeAnimal(animal){

         this.animals.splice(this.animals.indexOf(animal),1);


     },

     moveToTop(key){

         this.animals.unshift(this.animals.splice(key,1)[0])

     },

     addAnimal(){

         this.animals.push(this.newAnimal)

     }


 },
}
</script>
