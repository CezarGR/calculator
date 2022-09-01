<template>
    <div class="calculator">
        <DisplayVue />
        <ButtonVue label="C" :operationGrey="true"/>
        <ButtonVue label="+/-" :operationGrey="true"/>
        <ButtonVue label="%" :operationGrey="true"/>
        <ButtonVue label="C" :operation="true"/>
        <ButtonVue label="7" />
        <ButtonVue label="8" />
        <ButtonVue label="9" />
        <ButtonVue label="X" :operation="true"/>
        <ButtonVue label="4" />
        <ButtonVue label="5" />
        <ButtonVue label="6" />
        <ButtonVue label="-" :operation="true"/>
        <ButtonVue label="1" />
        <ButtonVue label="2" />
        <ButtonVue label="3" />
        <ButtonVue label="+" :operation="true"/>
        <ButtonVue label="0" :double="true"/>
        <ButtonVue label="," :operation="true"/>
        <ButtonVue label="=" :operation="true"/>
    </div>
</template>

<script>
import ButtonVue from '@/components/Button.vue';
import DisplayVue from '@/components/Display.vue';

export default {
    components: { ButtonVue, DisplayVue }
}
</script>

<style>
.calculator {
    padding: 2px;
    width: 235px;
    height: 320px;
    backdrop-filter: blur(3px) saturate(200%);
    -webkit-backdrop-filter: blur(3px) saturate(200%);
    background-color: rgba(17, 25, 40, 0.68);
    border-radius: 6px;
    border: 1px solid rgba(255, 255, 255, 0.125);

    display: grid;
    grid-template-columns: repeat(4, 25%);
    grid-template-rows: 1fr 48px 48px 48px 48px 48px;
}
</style>