<template>
    <div class="azhar">
        <label class="float-start">{{label}} <span >*</span></label>
        <input type="text" v-model="value" @change="e=>handleField(e)" :name="`${name}`" id="" >
    </div>
</template>

<script>


export default {
    props: ["name","label"],
    data () {
        return {
            value: ""
        }
    },

    methods:{
      handleField(e){
        //console.log(e.target.value,e.target.name)
        this.$emit('handleInput',e.target.value,e.target.name);
      }
    },
}
</script>

<style scoped>
input[type=text], select {
  width: 100%;
  padding: 12px 20px;

  /* margin: 8px 0; */
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
@media screen and (min-width: 600px) {
  .input {
    max-width:100px;
  }
}
</style>