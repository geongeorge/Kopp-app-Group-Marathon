<template>
  <div class="bg-white shadow w-full rounded mb-1 p-2">
      <a :href="url" target="_blank" class="hover:underline"><slot></slot></a>
  </div>
</template>

<script>
export default {
    props: {
        url: {default: "#"}
    }
}
</script>

<style>

</style>