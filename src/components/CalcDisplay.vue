<template>
    <div class="display">
        {{ value  }}
    </div>
</template>

<script>
    export default {
        props: [ 'value' ],
    }
</script>

<style>
.display {
    grid-column: span 4;
    background-color: rgba(0, 0, 0, 0.5);
    font-weight: 600;
    display:flex;
    justify-content: flex-end;
    align-items: center;
    padding: 20px;
    font-size: 2.1em;
    overflow: hidden;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
}
</style>