<template>
    <div v-if="!persons.length">No person available</div>
    <div :key="person.id" v-for="person in persons">
        <Person :person="person"
            @toggle-person="$emit('toggle-person', person.id)"
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
        emits: ['delete-person', 'toggle-person'],
    }
 </script>