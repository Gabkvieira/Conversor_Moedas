<script setup>
const props = defineProps(["numero1", "numero2", "trocarFiltro"]);
</script>

<template>
    <form>
        <div class="row">
            <div class="col d-flex">
            <input @keyup="props.numero1" required type="number" placeholder="Digite o valor a ser convertido" class="form-control border-dark">
            </div>
            <div class="col-md-4 alteraCelular">
                <select @change="props.trocarFiltro" class="alinhaTexto form-control border-dark">
                    <option value="pesoChilenoReal">Peso Chileno para Real</option>
                    <option value="dolarReal">Dólar para Real</option>
                    <option value="euroReal">Euro para Real</option>]
                    <option value="wonReal">Won para Real</option>
                    <option value="ieneReal">Iene para Real</option>
                    <option value="realPesoChileno">Real para Peso Chileno</option>
                    <option value="realDolar">Real para Dólar</option>
                    <option value="realEuro">Real para Euro</option>]
                    <option value="realWon">Real para Won</option>
                    <option value="realIene">Real para Iene</option>
                </select>
            </div>
        </div>
    </form>
</template>

<style scoped>
form input {
    margin-right: 16px;
    text-align: center;
}

.alinhaTexto {
    text-align: center;
}

@media only screen and (max-width: 767px) {
    .alteraCelular {
        margin-top: 16px;
    }

    form input {
    margin-right: 3px;
}
}
</style>