<template>
  <div class="door-area">
    <div class="door-frame" :class="{selected}">
        <TheGift v-if="open && hasGift"/>
    </div>
    <div class="door" :class="{open}" @click="selected = !selected">
        <div class="number" :class="{selected}">{{number}}</div>
        <div class="knob" :class="{selected}" @click.stop="open = true"></div>
    </div>
  </div>
</template>

<script>
import TheGift from "./TheGift.vue";

export default {
    nome: "TheDoor",

    components: { TheGift },

    props: {
        number: {}, // number of doors
        hasGift: { type: Boolean }
    },
    
    data: function() {
        return {
            open: false,      // the door starts closed and not selected
            selected: false
        }
    }
}
</script>

<style>

:root {
    --door-border: 10px solid brown;
    --selected-border: 10px solid yellow;
}

.door-area {
    position: relative;
    width: 220px;
    height: 315px;
    border-bottom: 15px solid rgb(83, 83, 83);
    margin: 20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;
}

.door-frame {
    position: absolute;
    height: 300px;
    width: 180px;

    border-left: var(--door-border);
    border-top: var(--door-border);
    border-right: var(--door-border);

    display: flex;
    justify-content: center;
    align-items: flex-end; 
}

.door {
    position: absolute;
    top: 10px;
    height: 290px;
    width: 160px;
    background-color: rgb(103, 0, 0);

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}

.door .knob {
    background-color: brown;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    align-self: flex-start;
    margin-top: 30px;
}

.door-frame.selected {
    border-left: var(--selected-border);
    border-top: var(--selected-border);
    border-right: var(--selected-border);
}

.door > .number {
    color: white;
    font-size: 5rem;
    padding-top: 15px;
}

.door > .number.selected {
    color: yellow;
}

.door > .knob.selected {
    background-color: yellow;
}

.door.open {
    background-color: #0007;
}

.door.open .knob {
    display: none;
}

.door.open .number {
    display: none;
}

</style>