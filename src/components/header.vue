<template>
        <div class="container mt-3">
      <h1>Formularios</h1>
      <hr>
      <Form />
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    import Form from './Form.vue';

    const name = ref("")
    const age = ref(0)
    const mail = ref("")
</script>