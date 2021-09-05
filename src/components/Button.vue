<template>
    <button @click="getPerson"
            :style="{ background: color}"
            class="btn">{{ text }}</button>
</template>

<script>
    export default {
        name: 'Button',
        props: {
            text: String,
            color: String,
            width: String
        }, 
        data() {
            return {
                id:'',
                firstName: '',
                lastName: '',
                email: '',
                gender: '',
                age: '',
                picture: '',
                dob: '',
                street: '',
                city: '',
                country: '',
                selected: false,
            }
        },
        methods: {
            async getPerson(){
                const res = await fetch("https://randomuser.me/api");
                const { results } = await res.json();
                console.log(results);

                if(results.length > 0){
                    let person = {
                        id: results[0].login.uuid,
                        firstName: results[0].name.first,
                        lastName: results[0].name.last,
                        email: results[0].email,
                        gender: results[0].gender,
                        age: results[0].dob.age + "yrs",
                        picture: results[0].picture.large,
                        dob: this.formatDate(results[0].dob.date),
                        selected: true,
                        street: results[0].location.street.number + " " + results[0].location.street.name,
                        city: results[0].location.city,
                        country: results[0].location.country,
                    }

                    console.log(person);
                    this.$emit('clicked', { person });
                }

                
            },
            formatDate(date) {
                var d = new Date(date),
                    month = "" + (d.getMonth() + 1),
                    day = "" + d.getDate(),
                    year = d.getFullYear();

                if (month.length < 2) month = "0" + month;
                if (day.length < 2) day = "0" + day;
                return [year, month, day].join("-");
            }
        }
    }
</script>

<style scoped>

</style>