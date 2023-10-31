<template>
    ini header
    <div>
        state: {{ counter }}
        <br />
        getters: {{ getCount }}
        <br />
        getters: {{ doubleCount }}
        <br />
        getters: {{ divideByTwo }}
        <br />
        pokemon: {{ pokemon }}
    </div>
</template>

<script setup>
import { computed } from 'vue'
import { useCounterStore } from '../stores/counter'
import { usePokemonStore } from '../stores/pokemon';

const counteStore = useCounterStore()
const pokemonStore = usePokemonStore()

const counter = computed(() => counteStore.count)
const getCount = computed(() => counteStore.getCount)
const doubleCount = computed(() => counteStore.doubleCount)
const divideByTwo = computed(() => counteStore.divideBy(2))

const pokemon = computed(() => pokemonStore.pokemonDetails)

counteStore.$subscribe((mutation, state) => {
    console.log(mutation, state)
})
</script>