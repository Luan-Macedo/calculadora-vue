<script setup>
import { reactive } from 'vue';

const estado = reactive({
    primeiroNumero: '',
    segundoNumero: '',
    operacao: {
        soma: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => a / b,
    },
    resultado: 0,
});

const calculo = () => {
    const { primeiroNumero, segundoNumero, operacaoMatematica } = estado;
    const num1 = parseFloat(primeiroNumero);
    const num2 = parseFloat(segundoNumero);
    estado.resultado = !isNaN(num1) && !isNaN(num2) ? estado.operacao[operacaoMatematica](num1, num2) : 'Número inválido';
};
</script>

<template>
    <div class="container">
        <header class="p-5 mb-4 mt-4">
            <h1>Calculadora utilizando VueJS</h1>
        </header>
        <form class="p-5">
            <div class="row">
                <div class="col-md-1">
                    <input type="number" class="form-control" v-model="estado.primeiroNumero" @input="calculo">
                </div>
                <div class="col-md-2">
                    <select v-model="estado.operacaoMatematica" class="form-control" @change="calculo">
                        <option value="soma">Soma</option>
                        <option value="subtracao">Subtração</option>
                        <option value="divisao">Divisão</option>
                        <option value="multiplicacao">Multiplicação</option>
                    </select>
                </div>
                <div class="col-md-1">
                    <input type="number" class="form-control" v-model="estado.segundoNumero" @input="calculo">
                </div>
                <div class="col-md-2 mt-1">
                    <p>= {{ estado.resultado }}</p>
                </div>
            </div>
        </form>
    </div>
</template>

<style>
</style>