<template>
  <div>

    <h1>List of animals in the local zoo</h1>

    <table>

      <thead>
      <th>Animal Type</th>
      <th>Name</th>
      <th>date of birth</th>

      </thead>

      <tbody>
      <tr v-for="animal in animals">

        <td>{{ animal.type }}</td>
        <td>{{ animal.name }}</td>
        <td>{{ animal.dateOfBirth }}</td>

      </tr>

      </tbody>



    </table>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
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


          ],



      }


 }
}
</script>
