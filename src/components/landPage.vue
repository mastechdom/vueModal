<template>
    <div class="container ex1">
        <div class="row">
            <div class="col-md-6">
                <h6 class="basic step-heading bold float-start"><b>Contact Information</b></h6>
            </div>
        </div>
        <div class="row">
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12">
                <p class="basic required-p float-start">
                    <span class="required-red">
                        *
                    </span>
                        Required
                    </p>
            </div>
        </div>
        <div class="row">
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12 mt-3">
                <InputFeild label="First Name" @handleInput="getValue" name="fname" />
            </div>
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12 mt-3">
                <InputFeild label="Last Name" @handleInput="getValue" name="lname"/>
            </div>
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12 mt-3">
                <InputFeild label="Email" @handleInput="getValue" name="email"/>
            </div>
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12 mt-3">
                <InputFeild label="Phone Number" @handleInput="getValue" name="mobile"/>
            </div>
        </div>
        <div class="row">
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12 mt-3">
                <span class="label label-default float-start" id="labletext"><b>My Offer </b></span>
                <span class="label label-default float-start italic" id="labletext2">
                Current Asking Price: $9,999</span
                >
            </div>
        </div>
        <div class="row">
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12">
                <InputFeild label="Enter Offer" @handleInput="getValue" name="myOffer"/>
            </div>
        </div>
        <div class="row">
            <div class="col-sm-12 col-lg-12 col-md-12 col-xs-12 mt-4">
                
                <Accordians @handleTrade="getValue1" />

            </div>
        </div>
    </div>
    <div class="footer">
        <hr style="width:95%;text-align:center;background-color:lightslategray">
        <button class=" col-sm-12 col-lg-6 col-md-6 col-xs-12 btn-submit" @click="submit()">Submit</button><br>
    </div>
    
</template>

<script>
import InputFeild from './inputField.vue'
import Accordians from './accordions.vue'
export default {
    data: () => {
        return {
            item: {},
            tradeItem: {},
        }
    },
    components: {
        InputFeild,
        Accordians,
    },
    methods: {
        submit() {
            this.$emit('close-submit',this.item,this.tradeItem)
        },
        getValue(value,name){
            if(name === "fname"){
                this.item.fname =  value;
            }
            if(name === "lname"){
                this.item.lname =  value;
            }
            if(name === "email"){
                this.item.email =  value;
            }
            if(name === "mobile"){
                this.item.mobile =  value;
            }
            if(name === "myOffer"){
                this.item.myOffer =  value;
            }
        },
        getValue1(value,name) {
          if(name === "years"){
            this.tradeItem.years =  value;
          }
          if(name === "make"){
            this.tradeItem.make =  value;
          }
          if(name === "model"){
            this.tradeItem.model =  value;
          }
          if(name === "condition"){
            this.tradeItem.condition =  value;
          }
          if(name === "milage"){
            this.tradeItem.milage =  value;
          }
          if(name === "vin"){
            this.tradeItem.vin =  value;
          }
          if(name === "message"){
            this.tradeItem.message =  value;
          }
        },
    }
}
</script>

<style scoped>
#heading-landPage {
    padding-left: 15px;
}
#labletext2 {
    color: gray;
    padding-left: 20px;
    font-family: italic;
}
.btn-submit {
    font-size: 20px;
    height: 50px;
    width: 300px;
    color: white;
    background: darkslategrey;
    border-radius: 5px;
}

.ex1 {
 
    width: 600px;
  height: 350px;
    overflow: auto;
    overflow-x: hidden;
}
::-webkit-scrollbar{
  width:0px;
}
::-webkit-scrollbar-thumb{
  background: #ff0000;
}


</style>
