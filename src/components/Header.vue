<template>
    <v-app-bar app>
        <v-toolbar-title class="headline text-uppercase mr-4">
            <span>Stock</span>
            <span class="font-weight-light">Trader</span>
        </v-toolbar-title>    
        <v-toolbar-items>
            <v-btn text to="/">Início</v-btn>
            <v-btn text to="/portfolio">Portfólio</v-btn>
            <v-btn text to="/stocks">Ações</v-btn>
        </v-toolbar-items>

        <v-spacer></v-spacer>

        <v-toolbar-items>
            <v-btn text @click="endDay">Finalizar Dia</v-btn>
            <v-menu offset-y>
                <template v-slot:activator="{on}">
                    <v-btn text v-on="on" >Salvar e Carregar</v-btn> <!-- FIX slot="activator" é um dropdown -->
                </template>
                <v-list>
                    <v-list-item-group>
                        <v-list-item @click="saveData">Salvar Dados</v-list-item>
                    </v-list-item-group>
                    <v-list-item-group>
                        <v-list-item @click="loadDataLocal">Carregar Dados</v-list-item>
                    </v-list-item-group>
                </v-list>
            </v-menu>
            <v-layout align-center>
                <span class="text-uppercase grey--text text--darken-2">
                    Saldo: {{ funds | currency }}
                </span>
            </v-layout>
        </v-toolbar-items>
    </v-app-bar>        
</template>

<script>
import { mapActions } from 'vuex'

export default {
    computed: {
        funds() {
            return this.$store.getters.funds
        }
    },
    methods: {
        ...mapActions(['randomizeStocks', 'loadData']),
        endDay() {
            this.randomizeStocks();
        },
        saveData() {
            const { funds, stockPortfolio, stocks} = this.$store.getters
            this.$http.put('data.json', {
                funds, stockPortfolio, stocks
            })
        },
        loadDataLocal() {
            this.loadData()
        }
    }

}
</script>

<style>

</style>
