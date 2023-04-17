<template>
  <div>
    <h1 class="text-center">Trabalhos</h1>
    <my-modal title="Lista de trabalhos" />
  </div>
</template>

<script>
import MyModal from "./components/Modal.vue";

export default {
  name: "MyApp",
  components: {
    MyModal,
  },
  data() {
    return {};
  },
};
</script>
<style></style>
