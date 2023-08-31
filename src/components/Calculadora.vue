<script setup>
    const props = defineProps(['num1', 'calcular', 'num2', 'resultadoCalculo', 'atualizarNum1', 'atualizarNum2', 'atualizarCalculo']);
</script>

<template>
    <form>
        <div class="row align-items-center">
            <div class="col-md-5 d-flex justify-content-center">
                <input @change="props.atualizarNum1" class="squareInput form-control" :value="props.num1" placeholder="0" type="number">
            </div>
            <div class="col-md d-flex justify-content-center">
                <select @change="props.atualizarCalculo" :value="props.calcular" class="funcaoAritmetica form-select">
                    <option value="soma">+</option>
                    <option value="subtracao">-</option>
                    <option value="multiplicacao">x</option>
                    <option value="divisao">÷</option>
                </select>
            </div>
            <div class="col-md-5 d-flex justify-content-center">
                <input @change="props.atualizarNum2" class="squareInput form-control" :value="props.num2" placeholder="0" type="number">
            </div>
        </div>
        <div class="resultado row">
            <div class="col text-center">
                <h2>Resultado:</h2>
                <span>{{ props.resultadoCalculo }}</span>
            </div>
        </div>
    </form>
</template>

<style scoped>
form {
    margin-top: 100px;
}

.squareInput {
    width: 100px;
    height: 100px;
    font-size: 32px;
    filter: drop-shadow(3px 3px 2px);
}

.funcaoAritmetica {
    width: 60px;
    height: 60px;
    font-size: 18px;
}

.resultado {
    margin: 0 auto;
    width: 400px;
}

.text-center {
    margin-top: 120px;
    border: 2px solid #99ff99;
    border-radius: 10px;
    padding-bottom: 15px;
}
</style>