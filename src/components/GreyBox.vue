<script>
export default {
    name: "GreyBox",
    props: {

        title: {
            type: String,
            required: true,
        },

        date: {
            type: String,
        },

         handleDelete: {
            type: Function,
        } 
/* 
        array */
    },
/* 
    methods: {
        handleDelete(array){

        }
    } */
}
</script>

<template>
    <div class="greyBoxContainer">
        <div class="textContainer">
        <span class="date">{{ date }}</span>
        <span class="title">{{ title }}</span>
        </div>
        <button class="deleteSkill" @click="handleDelete"></button>
    </div>
</template>

<style lang="scss" scoped>

.greyBoxContainer{
    display: flex;
    justify-content: space-between;
}

.textContainer{
    display: flex;
    flex-direction: column;
}
.deleteSkill{
    width: 30px;
    height: 30px;
    background-color: red;
}

</style>