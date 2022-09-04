<template>
    <div class="calculator">
        <DisplayVue v-model="displayValue" />
        <ButtonVue label="AC" :operationGrey=true @onClick="clearMemory"/>
        <ButtonVue label="+/-" :operationGrey="true" @onClick="setOperation"/>
        <ButtonVue label="%" :operationGrey="true" @onClick="setOperation"/>
        <ButtonVue label="/" :operation="true" @onClick="setOperation"/>
        <ButtonVue label="7"  @onClick="addDigt"/>
        <ButtonVue label="8"  @onClick="addDigt"/>
        <ButtonVue label="9"  @onClick="addDigt"/>
        <ButtonVue label="*" :operation="true" @onClick="setOperation"/>
        <ButtonVue label="4"  @onClick="addDigt"/>
        <ButtonVue label="5"  @onClick="addDigt"/>
        <ButtonVue label="6"  @onClick="addDigt"/>
        <ButtonVue label="-" :operation="true" @onClick="setOperation"/>
        <ButtonVue label="1"  @onClick="addDigt"/>
        <ButtonVue label="2"  @onClick="addDigt"/>
        <ButtonVue label="3"  @onClick="addDigt"/>
        <ButtonVue label="+" :operation="true" @onClick="setOperation"/>
        <ButtonVue label="0" :double="true" @onClick="addDigt"/>
        <ButtonVue label="." :operation="true" @onClick="addDigt"/>
        <ButtonVue label="=" :operation="true" @onClick="setOperation"/>
    </div>
</template>

<script>
import ButtonVue from '@/components/Button.vue';
import DisplayVue from '@/components/Display.vue';

export default {
    data: function() {
        return {
            displayValue: "0",
            clearDisplay: false,
            operation: null,
            values: [0, 0],
            current: 0
        }
    },
    components: { ButtonVue, DisplayVue },
    methods: {
        clearMemory() {
            Object.assign(this.$data, this.$options.data())
        },
        setOperation(operation) {
            console.log('o');

            if (this.current === 0) {
                this.operation = operation
                this.current = 1
                this.clearDisplay = true
            }
            else {
                const equals = operation === "="
                const currentOperation = this.operation

                try {
                    console.log( `${this.values[0]} ${currentOperation} ${this.values[1]}`)
                    const result = eval(
                        `${this.values[0]} ${currentOperation} ${this.values[1]}`
                    )

                    if (isNaN(result) || !isFinite(result)) {
                        this.clearMemory()
                        return
                    }

                    this.values[0] = result
                } catch (e) {
                    console.log(e);
                    this.$emit('onError', e);
                }

                this.values[1] = 0
                this.displayValue = this.values[0]
                this.operation = equals ? null : operation
                this.current = equals ? 0 : 1
                this.clearDisplay = !equals
            }
        },
        addDigt(n) {
            if (n === "." && this.displayValue.includes(".")) {
                return
            }

            const clearDisplay = this.displayValue === "0" || this.clearDisplay
            const currentValue = clearDisplay ? "" : this.displayValue
            const displayValue = currentValue + n

            this.displayValue = displayValue
            this.clearDisplay =  false

            if (n != ".") {
                const i = this.current
                const newValue = parseFloat(displayValue)
                this.values[i] = newValue
            }
        }
    }
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