<template>
    <div>
        <h1 class="display-3 font-weight-light mb-4">Negocie e Consulte suas Ações</h1>
        <v-sheet :elevation="6" class="pa-2 primary">
            <v-icon class="white--text mr-3">info</v-icon>
            <span class="headline white--text font-weight-light">
                Você pode Salvar $ Carregar os dados
            </span>
        </v-sheet>
        <v-sheet :elevation="6" class="pa-2 mt-3 success">
            <v-icon class="white--text mr-3">info</v-icon>
            <span class="headline white--text font-weight-light">
                Clique em finalizar dia para iniciar um novo dia
            </span>
        </v-sheet>
        <v-divider class="my-4" />
        <p class="display-1"><strong>Seu saldo:</strong> {{ funds | currency }} </p>
    </div>
</template>

<script>
export default {
    computed: {
        funds() {
            return this.$store.getters.funds
        }
    }
}
</script>

<style>

</style>
