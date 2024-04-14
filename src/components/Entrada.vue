<script>
export default {
    data() {
        return {
            value: 0
        };
    },
    novoValor: function (event) {
        this.value = parseFloat(event.target.value);
        this.$parent.calculate();
    }
};
</script>

<template>
    <input type="number" v-model="value" @input="novoValor" />
</template>