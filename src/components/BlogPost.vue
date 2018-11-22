<template>
    <div>
        <h3>{{title}}</h3>
        <button @click="functionInChild">Call parent function</button><br>
        {{message}}
        <br>
        {{getReversedMessageMethod()}}
        <br>
        {{reverseMessageComputed}}  
        <!-- poziva se kao properti -->
    </div>
</template>

<script>
export default {

    data() {
        return {
            message: 'Ovo je neka poruka'
        }
    },

    props: ['title'],

    methods: {
        functionInChild() {
            console.log('child function');
            this.$emit('callParentFunction', 'Jack', 29);
        },

        getReversedMessageMethod() {
            return this.message.split(' ').reverse().join(' ');
        }
    },

    computed: {
        reverseMessageComputed() {
            return this.message.split(' ').reverse().join(' ');
            // samo se jednom izvrsi i ne pozivamo ga jedino ako se promeni on ce ponovo
        }
    }
};
</script>

