<template>
    <div class="display">
        {{ value }}
    </div>
</template>

<script>
export default {
    props: [
        'value'
    ]
}
</script>

<style>
:root {
    --bg-button: transparent;
    --border-button: 1px solid white;
}

.display {
    padding: 20px;
    border: 1px solid white;
    border-radius: 4px;
    display: flex;
    flex-wrap: nowrap;
    flex-direction: column;
    justify-content: center;
    align-items: flex-end;
    grid-column: span 4;
    overflow: hidden;
}
</style>