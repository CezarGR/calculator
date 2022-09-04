<template>
    <button class="button"
        @click="$emit('onClick', label)"
        :class="{double, triple, operation, operationGrey}"
    >
        {{ label }}
    </button>
</template>

<script>
export default {
    props: {
        label: {},
        operationGrey: { type: Boolean },
        operation: { type: Boolean },
        double: { type: Boolean },
        triple: { type: Boolean }
    }
}
</script>

<style>
:root {
    --bg-button: transparent;
    --border-button: 1px solid white;
}

.button {
    margin: 1px;
    border: none;
    border-right: var(--border-button);
    border-bottom: var(--border-button);
    background-color: var(--bg-button);
    border-radius: 4px;
    outline: none;
    display: flex;
    flex-wrap: nowrap;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.button:active {
    background-color: rgba(255, 255, 255, 0.151)
}

.button.double {
    grid-column: span 2;
}

.button.triple {
    grid-column: span 3;
}

.button.operation {
    background-color: rgba(250, 170, 20, 0.137);
    border-right: 1px solid rgba(255, 166, 0, 0.692);
    border-bottom: 1px solid rgba(255, 166, 0, 0.692);
}

.button.operationGrey {
    background-color: rgba(109, 104, 96, 0.137);
    border-right: 1px solid rgba(226, 221, 213, 0.788);
    border-bottom: 1px solid  rgba(226, 221, 213, 0.788);
}

.button.operationGrey:active {
    background-color: rgba(114, 109, 101, 0.623);
    border-right: 1px solid rgba(255, 255, 255, 0.788);
    border-bottom: 1px solid rgba(255, 255, 255, 0.788);
}


.button.operation:active {
    background-color: rgba(255, 166, 0, 0.425);
    border-right: 1px solid rgb(255, 166, 0);
    border-bottom: 1px solid rgb(255, 166, 0);
}



</style>