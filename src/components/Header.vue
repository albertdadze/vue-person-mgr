<template>
    <header>
        <h1 :style="{ color: color}">{{ title }}</h1>        
        <Button @clicked="onAddPerson" text="Add Person" color="red" />
    </header>
    <hr style="border-top: 1px solid red;" />
</template>

<script>
    import Button from "./Button.vue";

    export default {
        name: 'Header', 
        props: {
            title: String,
            color: String,
        },
        components: {
            Button,
        },
        methods: {
            onAddPerson({ person }){
                //console.log(person);
                this.$emit('add-person', { person })
            }
        },
        emits: ['add-person'],
    }
</script>

<style>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>