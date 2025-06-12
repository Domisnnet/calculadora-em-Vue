<template>
    <div class="calculator">
        <CalcDisplay value="100"/>
        <AddButton label="AC" triple/>
        <AddButton label="/" operation/>
        <AddButton label="7"/>
        <AddButton label="8"/>
        <AddButton label="9"/>
        <AddButton label="*"  operation/>
        <AddButton label="4"/>
        <AddButton label="5"/>
        <AddButton label="6"/>
        <AddButton label="-" operation/>
        <AddButton label="1"/>
        <AddButton label="2"/>
        <AddButton label="3"/>
        <AddButton label="+" operation/>
        <AddButton label="0" double/>
        <AddButton label="."/>
        <AddButton label="=" operation/>
    </div>
</template>

<script>
import CalcDisplay from '../CalcDisplay.vue';
import AddButton from '../AddButton.vue';

export default {
    components: { AddButton, CalcDisplay }
}

</script>

<style>
.calculator {
    height: 320px;
    width: 235px;
    border-radius: 5px;
    overflow: hidden;
    display: grid;
    grid-template-columns: repeat(4, 25%);
    grid-template-rows: 1fr 48px 48px 48px 48px 48px;
}
</style>