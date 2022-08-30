<template>
    <div
        v-if="sign === 'positif'"
        v-on:click="emitincrement"
    >
        <span >+</span> 
        <span>{{ amount }}</span>
    </div>
    <div
        v-else
        v-on:click="emitdecrement"
    >
        <span >-</span> 
        <span>{{ amount }}</span>   
    </div>
</template>

<script>
export default {
    emits: [
        'asktoincrement',
        'asktodecrement'
    ],
    props: {
        sign: String,
        amount: Number
    },
    methods : {
        emitincrement(){
            console.log(this.amount)
            this.$emit('asktoincrement', this.amount)
        },
        emitdecrement(){
            this.$emit('asktodecrement', this.amount)
        }
    }
}
</script>

<style scoped>
    div{
        font-size: 1.5rem;
        margin: 1em 0;
    }
</style>