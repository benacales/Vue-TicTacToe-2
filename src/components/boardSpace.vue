<template>
<div class = "box">
    <button class = "theBox" @click = "makemove" type = "button" >
    <i class = "fa" :class = "{'fa-times':value === 1,'fa-circle-thin':value === 2}"></i>

    <!-- <h3 v-if = "value === 2">o</h3>
    <h3 v-else-if = "value === 1">x</h3> -->

    </button>
</div>
</template>

<script>
export default {
    props: ['value' , 'position'],
    name: "BoardSpace",
    methods: {
        makemove(e) {
            console.log ("this top posititon" , this.position)
            this.$emit("makeMove", this.position) // stuff
            // console.log (this.position);
        }
    }
}
</script>