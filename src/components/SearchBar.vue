<template>
    <div class="col-md-8 my-auto">
        <input @input="onInput" />
    </div>
</template>

<script>
  export default {
    name: 'SearchBar',
    methods: {
      onInput : function(event) {
        this.$emit('termChange', event.target.value);
      }
    }
  };
</script>

// Scoped keeps styling limited to this component
<style scoped>
    input {
        width: 100%;
    }
</style>