<template>
    ini footer
    <br />
    <button @click="increment">increment +</button>
    <button @click="decrement">decrement -</button>
    <button @click="reset">reset</button>
    <br />
    <button @click="incrementWithAction">incrementWithAction</button>
    <button @click="decrementWithAction">decrementWithAction</button>
    <button @click="incrementByWithAction(5)">incrementByWithAction</button>
    <hr />
    <button @click="fetchPokemon('ditto')">fetch ditto</button>
    <button @click="resetPokemon">reset pokemon</button>
</template>

<script setup>
import { useCounterStore } from '../stores/counter';
import { usePokemonStore } from '../stores/pokemon'

const counter = useCounterStore()
const pokemon = usePokemonStore()

const increment = () => {
    counter.$patch((state) => {
        state.count++
    })
}
const decrement = () => {
    counter.$patch((state) => {
        state.count--
    })
}
const reset = () => {
    counter.$reset()
}

const incrementWithAction = () => {
    counter.increment()
}
const decrementWithAction = () => {
    counter.decrement()
}
const incrementByWithAction = (amount) => {
    counter.incrementBy(amount)
}

const fetchPokemon = (name) => {
    pokemon.getPokemonDetails(name)
}
const resetPokemon = () => {
    pokemon.$reset()
}
</script>