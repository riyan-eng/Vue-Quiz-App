<template>
    <div>
        <button @click="$emit('select','+')">Penjumlahan (+)</button>
        <button @click="$emit('select','-')">Pengurangan (-)</button>
        <button @click="$emit('select','/')">Pembagian (/)</button>
        <button @click="$emit('select','*')">Perkalian (*)</button>
    </div>
</template>

<script>
export default {
    name: 'OperatorSelect'
}
</script>

<style scoped>

</style>