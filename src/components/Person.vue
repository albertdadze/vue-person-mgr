<template> 
    <div @dblclick="$emit('toggle-person', person.id)" :class="[person.selected ? 'selected': '','person']">
      <div class="row">
          <div class="col-sm-3 no-padding no-margin">
              <img :class="person.gender" 
                   :src="person.picture" 
                   :alt="`${person.firstName} ${person.lastName}`" />
          </div>
          <div class="col-sm-9">            
            <h3>                     
                {{ person.firstName }} {{ person.lastName }}
                <i 
                    class="fas fa-times"
                    @click="$emit('delete-person', person.id)"></i> 
           </h3>
            <p class="no-padding no-margin">{{ person.email}}</p>
            <p class="no-padding no-margin">{{ person.dob }} {{ person.age }}</p>
            <p class="no-padding no-margin">{{ person.street }}, {{ person.city }}, {{ person.country }}</p>
          </div>
      </div>       
    </div>   
</template>

<script>
    export default {
        name: 'Person',
        props:{
            person: Object
        }
    }
</script>

<style>
    .fas {
        color: red;
    }

    .person {
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }

    .person.selected {
        border-left: 5px solid green;
    }

    .person h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .male {
        border-color: steelblue;
        background-color: steelblue;
    }

    .female {
        border-color: pink;
        background-color: pink;
        color: #333;
    }

    img {
        border-radius: 50%;
        border: 5px #333 solid;
        margin-bottom: 1rem;
    }
</style>