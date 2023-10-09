<template>
    <div>
        <p>{{ error.statusCode }}</p>
        <p> Ooops...</p>
        <p> {{ error.message }}</p>
        <p>It looks like something broke.</p>
      <p>Sorry about that.</p>
      <p>
            <a @click="handleError">
                Click to go back Home.
            </a>
          </p>
    </div>
</template>

<script setup>
const error = useError();

const handleError = () => {
  clearError({
    redirect: '/',
  });
};
</script>

<style lang="scss" scoped>

</style>