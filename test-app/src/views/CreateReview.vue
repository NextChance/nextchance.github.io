<script setup>
import { useGlobalStore } from "../stores/global-store";
import CreateReviewForm from "../components/CreateReviewForm.vue";
import GoogleLogin from "../components/GoogleLogin.vue";
import { onMounted } from "vue";

const globalStore = useGlobalStore();
onMounted(async () => {
  await globalStore.loginApp();
});
</script>

<template>
  <div class="create-review">
    <h1>Create Review for Docamar(0558c2a4-dc7d-4a57-bc79-b59999d472e0)</h1>
    <p v-if="!globalStore.user">
      <em style="font-weight: bold; color: red"
        >Recuerda que necesitas identificarte como usuario para crear una
        review</em
      >
      <google-login></google-login>
    </p>
    <create-review-form v-else></create-review-form>
  </div>
</template>

<style>
hr {
  margin-top: 1rem;
}
</style>
