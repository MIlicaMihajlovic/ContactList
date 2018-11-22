<template>
    <div>

        <ContactListTable :contactList="contacts" />


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
                <ContactDetails :contact="routeContact" />
        </div>
      
       
    </div>
</template>

<script>

import ContactListTable from './ContactListTable';
import ContactDetails from './ContactDetails';

export default {

    components: {
        ContactListTable,
        ContactDetails
    },

    data() {
        return {
            newContact: {
                firstName: '',
                lastName: '',
                email: '',
            },
            contacts: [
                {id: 1, firstName: 'John', lastName: 'Doe', email: 'example@example.com'},
                {id: 2, firstName: 'Jack', lastName: 'Doe', email: 'example@example.com'},
                {id:3, firstName: 'Ann', lastName: 'Doe', email: 'example@example.com'},
                {id: 4, firstName: 'Jasmin', lastName: 'Doe', email: 'example@example.com'},
                {id: 5, firstName: 'Susan', lastName: 'Doe', email: 'example@example.com'}
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
    },

    computed: {
        routeContact() {
            let findedContact = this.contacts.find(contact => contact.id == this.$route.params.id);
            console.log(findedContact);
            return findedContact;
        }
        
    }
};

</script>

