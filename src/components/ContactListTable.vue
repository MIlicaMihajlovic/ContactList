<template>
    <div>
        <h3>Contact List</h3>

        <table border=1>
            <thead>
                <th>KEY</th>
                <th>Name</th>
                <th>Email</th>
                <th></th>
            </thead>
            <tbody>
                <tr v-for="(contact, index) in contactList" :key="index">
                    <td>{{ index + 1 }}</td>
                    <td>
                        <router-link :to="{name: 'contact-details', params: {id: contact.id}}">
                            {{ contact.firstName }} {{ contact.lastName }}
                        </router-link>
                    </td>
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
    props: ['contactList']
};
</script>

