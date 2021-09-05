<template>
    <header>
        <h1 :style="{ color: color}">{{ title }}</h1>        
        <Button @clicked="onButtonClicked" text="Add Person" color="red" />
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
            onButtonClicked({ person }){
                //console.log(person);
                this.$emit('add-person', { person })
            }
        }
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