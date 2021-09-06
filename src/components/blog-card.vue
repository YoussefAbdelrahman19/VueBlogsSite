<template>
<div class="card">
  <div class="card-title">User Id is {{ data.id }}</div>
  <div>User Title is {{ data.title }}</div>
  <div>User Body is {{ data.body }}</div>
</div>

</template>

<script>
export default {
  props: {
    data: { required: true },
  },
};
</script>

<style>
</style>
