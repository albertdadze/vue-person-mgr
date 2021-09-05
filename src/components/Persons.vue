<template>
    <div v-if="!persons.length">No person available</div>
    <div :key="person.id" v-for="person in persons">
        <Person :person="person" 
           @delete-person="$emit('delete-person', person.id)" />
    </div>
</template>

<script>
    import Person from "./Person.vue";

    export default {
        name: 'Persons',
        props: {
            persons: Array,
        }, 
        components: {
            Person,
        },
        emits: ['delete-person'],
    }
 </script>