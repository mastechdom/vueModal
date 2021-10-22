<template>
<label class="float-start">{{label}} <span >*</span></label>
<div class="input-group mb-3">           
  <select class="form-select" :name="`${name}`" @change="e=>getDD(e)" id="inputGroupSelect01">
    <option selected>{{label}}</option>
    <option v-for="year in yearsArr" :key="year">{{ year }}</option>
  </select>
</div>
</template>

<script>
export default {
  props: ["name","yearsArr","label"],
  methods:{
    getDD(e){
      this.$emit('handleDD',e.target.value,e.target.name);
    }
  }
};
</script>

<style scoped>
input[type="text"], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  padding-top: 10px;
}
</style>
