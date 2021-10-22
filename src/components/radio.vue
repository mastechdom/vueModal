<template>
    <form>
        <label class="float-start">
        <input type="radio" name="{{name}}" >
        <span class="checkmark"></span>{{label}}
        </label>
    </form>
</template>

<script>

export default {
    props: {
        label: String,
        name : String,
    },
}
</script>

<style scoped>
input[type=text], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: flex;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
</style>