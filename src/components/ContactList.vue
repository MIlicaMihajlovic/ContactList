<template>
    <div>
        <h3>Contact List</h3>
        <table border=1>
            <thead>
                <th>KEY</th>
                <th>First Name</th>
                <th>Last Name</th>
                <th>Email</th>
            </thead>
            <tbody>
                <tr v-for="(contact, index) in contacts" :key="index">
                    <td>{{ index + 1 }}</td>
                    <td>{{ contact.firstName }}</td>
                    <td>{{ contact.lastName }}</td>
                    <td>{{ contact.email }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    data() {
        return {
            contacts: [
                {firstName: 'John', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Jack', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Ann', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Jasmin', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Susan', lastName: 'Doe', email: 'example@example.com'}
            ]
        };
    }
};
</script>

