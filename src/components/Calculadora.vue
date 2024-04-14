<script>
import InputField from './Entrada.vue';

export default {
    components: {
        InputField
    },
    data() {
        return {
            num1: 0,
            num2: 0,
            operation: 'soma',
            total: 0
        };
    },
    methods: {
        calculate() {
            const contas = {
                'soma': (num1, num2) => num1 + num2,
                'sub': (num1, num2) => num1 - num2,
                'vez': (num1, num2) => num1 * num2,
                'div': (num1, num2) => num1 / num2
            };

            var result = contas[this.operation](this.num1, this.num2);
            if (typeof result !== 'undefined') {
                this.total = result;
            } else {
                this.total = 0;
            }
        }
    }
};
</script>

<template>
    <div class="container">
        <header class="header p-3 mb-4 mt-4">
        <b>CALCULADORA ARITMÉTICA</b>
        </header>

    <div class="calculadora">
        <input-field class="calculadora__input1" v-model="num1" @change="calculate" /> <br /><br />
        <select v-model="operation" @change="calculate"> 
            <option value="soma">Somar</option>
            <option value="sub">Subtratir</option>
            <option value="vez">Multiplicar</option>
            <option value="div">Dividir</option>
        </select> <br /> <br />
        <input-field class="calculadora__input2" v-model="num2" @change="calculate" /> <br /><br />

    </div>
    <div class="resultado">O resultado é: {{ total }}</div>
    </div>
</template>

<style scoped>

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        list-style: none;
        text-align: center;

    }
    .header {
        background-color: #E7EAEF;
        font-size: 24px;
        border-radius: 10px;
    }
    .calculadora {
        align-items: center;
        padding: 40px;
        background-color: #217074;
        border-radius: 40px;
    }
    .calculadora__input1 {
        color: #217074;
    }

    .calculadora__input2 {
        color: #217074;
    }

    .resultado {
        margin-top: 10px;
        background-color: #E7EAEF;
        padding: 10px;
        font-size: 24px;
    }

</style>