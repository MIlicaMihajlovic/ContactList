<template>
    <div>
        <h3>Add contact</h3>

         <div>
             <!-- submit.prevent sprecava da se relouduje stranica nakon submit dugmeta kad klikne user -->
            <form @submit.prevent="addContact">
                <label>First Name</label>
                <input v-model="newContact.firstName" placeholder="First Name"/><br>
                <p>{{ firstName }}</p>

                <label>Last Name</label>
                <input v-model="newContact.lasttName" placeholder="Last Name"/><br>
                <p>{{ lastName }}</p>

                <label>Email</label>
                <input v-model="newContact.email" placeholder="Email"/><br>
                <p>{{ email }}</p>

                <button type="submit">ADD CONTACT</button>
            </form>

        </div>
        
        <h3>Contact List</h3>

        <table border=1>
            <thead>
                <th>KEY</th>
                <th>First Name</th>
                <th>Last Name</th>
                <th>Email</th>
                <th></th>
            </thead>
            <tbody>
                <tr v-for="(contact, index) in contacts" :key="index">
                    <td>{{ index + 1 }}</td>
                    <td>{{ contact.firstName }}</td>
                    <td>{{ contact.lastName }}</td>
                    <td>{{ contact.email }}</td>
                    <td>
                        <button class="btn btn-danger" @click="removeContact(contact)">Remove</button>
                    </td>
                </tr>
            </tbody>
        </table>
       
    </div>
</template>

<script>
export default {
    data() {
        return {
            newContact: {
                firstName: '',
                lastName: '',
                email: '',
            },
            contacts: [
                {firstName: 'John', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Jack', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Ann', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Jasmin', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Susan', lastName: 'Doe', email: 'example@example.com'}
            ],

        };
    },

    methods: {
        addContact() {
            this.contacts.push(this.newContact);
            //dodali smo u listu novokreirani 
            this.newContact = {}
            //ocistili smo objekat i bude prazan 
        },

        removeContact(contact) {
             //console.log(contact)
            let index = this.contacts.indexOf(contact);
            //console.log(index);
            this.contacts.splice(index, 1);
          // this.contacts.splice((this.contacts.indexOf(contact)), 1); moze u jednoj liniji koda
        }
    }
};

</script>

