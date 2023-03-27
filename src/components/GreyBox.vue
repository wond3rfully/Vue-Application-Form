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
    },
    methods: {
        handleDelete() {
            this.$emit("delete")
        }
    }
}
</script>

<template>
    <div class="greyBoxContainer">
        <div class="textContainer">
        <span class="date">{{ date }}</span>
        <span class="title">{{ title }}</span>
        </div>
        <a class="deleteSkill" @click="handleDelete">
        <img src="../../public/delete.png" alt=""></a>
    </div>
</template>

<style lang="scss" scoped>
/* 
.greyBoxContainer{
    display: flex;
    align-items: center;
gap: 16px;
width: 100%;
margin-left: 17px;
}

.textContainer{
    height: 25px;
width: 234px;
display: flex;
    flex-direction: column;
background-color: #DDE3EB;

} */


</style>