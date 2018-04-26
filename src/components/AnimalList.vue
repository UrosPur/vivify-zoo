<template>
    <div>

        <h4>add another animal to our zoo</h4>

        <form @submit.prevent="addAnimal">

            <label>Add animal type</label>
            <input v-model="newAnimal.type" type="text" placeholder="animal type"/>
            <p> {{ newAnimal.type }}</p>

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
                <td v-else> Nepoznat</td>
                <td>
                    <button @click="removeAnimal(animal)">remove</button>
                </td>
                <td>
                    <button @click="moveToTop(key)">move to the top</button>
                </td>

            </tr>

            </tbody>


        </table>

        <div style="padding-top: 50px">

            <button @click="disabelButton" :disabled="isButtonDisabled"> random button</button>

        </div>

        <div style="padding-top: 50px">

            <!--<button @click="setInterval(areYouSure(),3000)"> {{ buttonName }}</button>-->
            <button @click="areYouSure"> {{ buttonName }}</button>

        </div>

    </div>
</template>

<script>
    export default {
        name: 'AnimalList',
        data() {

            return {


                isButtonDisabled: false,

                buttonName: 'confirm',

                animals: [

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

                newAnimal: {

                    type: '',
                    name: '',
                    dateOfBirth: '',
                }


            }


        },

        methods: {

            removeAnimal(animal) {

                this.animals.splice(this.animals.indexOf(animal), 1);


            },

            moveToTop(key) {

                this.animals.unshift(this.animals.splice(key, 1)[0])

            },

            addAnimal() {

                this.animals.push(this.newAnimal)

            },

            //https://stackoverflow.com/questions/37465289/how-to-set-timeout-in-a-vuejs-method

            disabelButton() {

                this.isButtonDisabled = true;

                setTimeout(function () {
                    this.isButtonDisabled = false

                }, 5000)
            },

            areYouSure() {

                var result = confirm('are You sure?');

                if (result) {

                    this.buttonName = 'Success'

                    setTimeout(() => {

                    this.buttonName = 'confirm'

                    }, 3000)

                } else {


                        this.buttonName = 'you must confirm to finish'

                    setTimeout(() => {

                        this.buttonName = 'confirm'

                    }, 3000)

                }


                // setTimeout(() => {
                //
                // }, 3000)

            }


        }


    }
</script>
