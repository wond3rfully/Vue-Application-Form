<script>

export default {
    name: "InputFields",

    data() {
        return{
            firstName: "",
            lastName: "",
            age: ""
        }
    },
}
</script>

<template>

<div class="inputField">

    <input type="text" placeholder="Firstname" v-model="firstName" >
    <input type="text" placeholder="Lastname" v-model="lastName" >
    <input type="text" placeholder="Age" v-model="age" >

</div>

</template>