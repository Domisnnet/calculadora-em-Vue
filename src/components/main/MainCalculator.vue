<template>
    <div class="calculator">
        <CalcDisplay :value="displayValue"/>
        <AddButton label="AC" triple @onClick="ClearMemory"/>
        <AddButton label="/" operation @onClick="setOperation"/>
        <AddButton label="7" @onClick="addDigit"/>
        <AddButton label="8" @onClick="addDigit"/>
        <AddButton label="9" @onClick="addDigit"/>
        <AddButton label="*"  operation @onClick="setOperation"/>
        <AddButton label="4" @onClick="addDigit"/>
        <AddButton label="5" @onClick="addDigit"/>                  
        <AddButton label="6" @onClick="addDigit"/>
        <AddButton label="-" operation @onClick="setOperation"/>
        <AddButton label="1" @onClick="addDigit"/>
        <AddButton label="2" @onClick="addDigit"/>
        <AddButton label="3" @onClick="addDigit"/>
        <AddButton label="+" operation @onClick="setOperation"/>
        <AddButton label="0" double @onClick="addDigit"/>
        <AddButton label="." @onClick="addDigit"/>
        <AddButton label="=" operation @onClick="setOperation"/>
    </div>
</template>

<script>
import CalcDisplay from '../CalcDisplay.vue';
import AddButton from '../AddButton.vue';

export default {
    data() {
        return {
            displayValue: '0',
            ClearDisplay: false,
            operation: null,
            values: [0, 0],
            current: 0,
        };
    },
    components: { AddButton, CalcDisplay },
    methods: {
        ClearMemory() {
            Object.assign(this.$data, this.$options.data());
        },
        SetOperation(operation) {
            if (this.current === 0) {
                this.operation = operation;
                this.current = 1;
                this.ClearDisplay = true;
            }else {
                const equals = operation === '=';
                const currentOperation = this.operation;

                try {
                    this.values[0] = eval(`${this.values[0]} ${currentOperation} ${this.values[1]}`);   
                } catch (e) {
                    this.$emit('onError', e)
                }

                this.values[1] = 0;
                this.displayValue = this.values[0]
                this.operation = equals ? null : operation;
                this.current = equals ? 0 : 1;
                this.ClearDisplay = equals;
            }

            if (this.operation === '=' && this.current === 1) {
                this.current = 0;
            }

            if (this.values[0] === 0 && operation !== '=') {
                return;
            }

            if (this.operation && this.current === 1) {
                const result = eval(`${this.values[0]} ${this.operation} ${this.values[1]}`);
                this.values[0] = result;
                this.displayValue = String(result);
                this.ClearDisplay = true;
            } else {
                this.displayValue = String(this.values[this.current]);
            }

            this.operation = operation;
        },
        AddDigit(n) {
            if (n === '.' && this.displayValue.includes('.')) {
                return;
            }

            const ClearDisplay = this.displayValue === '0' || this.ClearDisplay;
            const currentValue = ClearDisplay ? '' : this.displayValue;
            const displayValue = currentValue + n;

            this.displayValue = displayValue;
            this.ClearDisplay = false;
            this.values[this.current] = parseFloat(displayValue) || 0;

            /*if (n !== '.') {
                const index = this.current;
                this.values[index] = parseFloat(displayValue);
                this.current = index === 0 ? 1 : 0;
            } */
        },
    },
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