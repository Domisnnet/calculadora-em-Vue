<template>
    <div class="calculator">
        <CalcDisplay />
        <AddButton />
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