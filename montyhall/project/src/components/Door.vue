<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected :selected && !open }">
            <Gift v-if="open && hasGift"/>
        </div>

        <div class="door" :class="{open}" 
             @click="selected = !selected"> 
            <div class="number" :class="{ selected }" >{{ number }}</div>
            <div class="knob" :class="{ selected } " @click.stop=" open = true "></div>
        </div>
    </div>
</template>

<script>
import Gift from './Gift'
export default {
    name: 'Door',
    components:{Gift},

    props:{
            number:{},
            hasGift:{type:Boolean},
    },

    data: () => ({
      open: false,
      selected: false,
    })

    }
</script>

<style>
    :root{
        --door-border:5px solid  brown;
        --selected-border: 5px solid yellow;
    }


.door-area{
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 10px solid #AAA;
    margin-top: 20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;
}

.door-frame{
        position: absolute;
        height: 300px;
        width: 180px;
        border: var(--door-border);

        display: flex;
        justify-content: center;
        align-items: center;
}
.door{
    position: absolute;
    top: 6px;
    height: 295px;
    width: 170px;
    background-color: mediumslateblue;

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 15px;
}

.door .knob{
        height: 20px;
        width: 20px;
        border-radius: 10px;
        background-color: midnightblue;
        align-self: flex-start;
        margin-top: 60px;

}

.door-frame.selected{
        border: var(--selected-border);
}
.door >.number.selected{
    color: yellow;
}
.door > .knob.selected {
    background-color: yellow;
}

.door.open
{
    background-color: azure;
}
.door.open .knob {
    display: none;
}
.door.open .number{
    display: none;
}
</style>