<template>
    <div :style="{ '--image-url': 'url(' + randomImg + ')' }" :class="[isFirst ? 'reverse' : '', 'center', 'player']">
        <div id="playerInfos">
            <div class="life" >{{ hp }}</div>
            <div class="positive half">
                <Button 
                    sign="positif"
                    :amount=500
                    v-on:asktoincrement="increment"
                />
                <Button 
                    sign="positif"
                    :amount=400
                    v-on:asktoincrement="increment"
                />
                <Button 
                    sign="positif"
                    :amount=300
                    v-on:asktoincrement="increment"
                />
                <Button 
                    sign="positif"
                    :amount=200
                    v-on:asktoincrement="increment"
                />
                <Button 
                    sign="positif"
                    :amount=100
                    v-on:asktoincrement="increment"
                />
            </div>
            <div class="negative half">
                <Button 
                    sign="negatif"
                    :amount=500
                    v-on:asktodecrement="decrement"
                />
                <Button 
                    sign="negatif"
                    :amount=400
                    v-on:asktodecrement="decrement"
                />
                <Button 
                    sign="negatif"
                    :amount=300
                    v-on:asktodecrement="decrement"
                />
                <Button 
                    sign="negatif"
                    :amount=200
                    v-on:asktodecrement="decrement"
                />
                <Button 
                    sign="negatif"
                    :amount=100
                    v-on:asktodecrement="decrement"
                />
            </div>
        </div>
    </div>
</template>

<script>
import Button from './Button.vue'
export default {
    components: {
        Button
    },
    props: {
        isFirst: Boolean,
    },
    data(){
        return {
            hp: 4000
        }
    },
    computed: {
        randomImg() {
            let randomInt = Math.floor(Math.random() * 10)
            let image = '../img/'+randomInt+'.jpg'
            return image
        }
    },
    methods: {
        decrement(amount) {
            console.log(amount)
            this.hp -= amount
        },
        increment(amount) {
            console.log(amount)
            this.hp = this.hp += amount
        },
    }    
}
</script>

<style scoped>

    .center {
        text-align:center;
        width:100%;
        margin:auto
    }

    #playerInfos {
        background-color: rgba(0, 0, 0, 0.5);
        height:100%;
        padding-top: 2em;
    }

    .player {
        background-image: var(--image-url);
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
    }

    .reverse {
        transform: rotate(180deg);
    }

    .life {
        color:aliceblue
    }

    .half {
        display: inline-block;
        width:50%
    }

    .positive {
        color: #27ae60
    }

    .negative {
        color: #c0392b
    }
</style>