<template>
    <button class="button"
        :class="{ double, triple, operation }">
        {{ label }}
    </button>
</template>

<script>
export default {
    props: {
        label: {}, 
        operation: { type: Boolean }, 
        double: { type: Boolean }, 
        triple: { type: Boolean } 
    }
}
</script>

<style>
.button {
    font-size: 1.4em;
    font-weight: bold;
    background-color: #f0f0f0;
    border: none;
    border-right: 1px solid #888;
    border-bottom: 1px solid #888;
    outline: none;
    cursor: pointer;
}

.button:active {
    background-color: #ccc;
}

.button.double {
    grid-column: span 2;
}

.button.triple {
    grid-column: span 3;
}

.button.operation {
    background-color: #fa8231;
    color: #fff;
}

.button.operation:active {
    background-color: #fa8231cc;
}
</style>