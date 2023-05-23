<template>
    <div>
        <button type="button" v-on:click="$emit('changeOperator','+')">Addition (+)</button>
        <button type="button" v-on:click="$emit('changeOperator','-')">Substraction (-)</button>
        <button type="button" v-on:click="$emit('changeOperator','*')">Multiplication (×)</button>
        <button type="button" v-on:click="$emit('changeOperator','/')">Division (÷)</button>
    </div>
</template>
<script>
export default {
    
}
</script>