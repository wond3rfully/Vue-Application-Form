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
        <a class="deleteSkill" @click="handleDelete"></a>
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