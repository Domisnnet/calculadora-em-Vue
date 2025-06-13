<template>
    <div class="calculator">
        <CalcDisplay :value="displayValue"/>
        <AddButton label="AC" triple @onClick="clearMemory"/>
        <AddButton label="/" operation @onClick="setOperation($event)"/>
        <AddButton label="7" @onClick="addDigit($event)"/>
        <AddButton label="8" @onClick="addDigit($event)"/>
        <AddButton label="9" @onClick="addDigit($event)"/>
        <AddButton label="*"  operation @onClick="setOperation($event)"/>
        <AddButton label="4" @onClick="addDigit($event)"/>
        <AddButton label="5" @onClick="addDigit($event)"/>                  
        <AddButton label="6" @onClick="addDigit($event)"/>
        <AddButton label="-" operation @onClick="setOperation($event)"/>
        <AddButton label="1" @onClick="addDigit($event)"/>
        <AddButton label="2" @onClick="addDigit($event)"/>
        <AddButton label="3" @onClick="addDigit($event)"/>
        <AddButton label="+" operation @onClick="setOperation($event)"/>
        <AddButton label="0" double @onClick="addDigit($event)"/>
        <AddButton label="." @onClick="addDigit($event)"/>
        <AddButton label="=" operation @onClick="setOperation($event)"/>
    </div>
</template>

<script>
import CalcDisplay from '../CalcDisplay.vue';
import AddButton from '../AddButton.vue';

export default {
    data() {
        return {
            displayValue: '0',
            clearDisplay: false, 
            operation: null,
            values: [0, 0],
            current: 0,
        };
    },
    components: { AddButton, CalcDisplay },
    methods: {
        clearMemory() {
            // A forma mais simples de resetar o estado em Vue
            Object.assign(this.$data, this.$options.data());
        },
        setOperation(operation) {
            if (this.current === 0) {
                this.operation = operation;
                this.current = 1;
                this.clearDisplay = true;
            } else {
                const equals = operation === '=';
                const currentOperation = this.operation;

                try {
                    // Calcula o valor usando os dados atuais
                    this.values[0] = eval(`${this.values[0]} ${currentOperation} ${this.values[1]}`);
                } catch (e) {
                    this.$emit('onError', e)
                }

                this.values[1] = 0;
                this.displayValue = this.values[0];
                this.operation = equals ? null : operation;
                this.current = equals ? 0 : 1;
                this.clearDisplay = true;
            }
        },
        addDigit(n) {
            // Impede a adição de múltiplos pontos
            if (n === '.' && this.displayValue.includes('.')) {
                return;
            }

            // Define se o display deve ser limpo antes de adicionar o novo dígito
            const shouldClearDisplay = this.displayValue === '0' || this.clearDisplay;
            const currentValue = shouldClearDisplay ? '' : this.displayValue;
            const newDisplayValue = currentValue + n;

            this.displayValue = newDisplayValue;
            this.clearDisplay = false;

            // Atualiza o array 'values(valores)' com o número atual do display
            this.values[this.current] = parseFloat(newDisplayValue);
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