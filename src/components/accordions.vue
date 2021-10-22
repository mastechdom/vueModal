<template>
    <div class="container">
      <div class="row" @click="toggle1">
        <div class="col-8">
          <span class="motor"><i class='fas fa-motorcycle'></i></span>
          <b>Have a Trade-in ?</b><span>(Optional)</span>
        </div>
        <div class="col-4">
          <span v-if="!openAccordion">
            <i class="fas fa-angle-down"></i>
          </span>
          <span v-if="openAccordion">
            <i class="fas fa-angle-up"></i>
          </span>
        </div> 
      </div>
      <div class="panel--body mt-4" v-if="visible1">
        <div class="row ">
            <div class="col-3 ">
              <button @click="noTrade()" class="no-trade-button" id="button-trade">No Trade In</button>
            </div>
            <div class="col-3">
              <button @click="tradeIn()" class="yes-trade-button" id="button-trade">Yes, I have A Trade-In</button>
            </div>
        </div>
        <div class="row mt-4" v-if="showTrade">
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12">
                <DropDown label="Select Year" @handleDD="getValue" :yearsArr="yearsArr" name="years"/>
            </div>
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12">
                <input-field label="Make" @handleInput="getValue" name="make"/>
            </div>
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12">
                <input-field label="Model" @handleInput="getValue" name="model"/>
            </div>
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12">
                <DropDown label="Condition" :yearsArr="condition" @handleDD="getValue" name="condition"/>
            </div>
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12">
                <input-field label="Estimated Milage" @handleInput="getValue" name="milage"/>
            </div>
            <div class="col-sm-12 col-lg-6 col-md-6 col-xs-12">
                <input-field label="VIN" @handleInput="getValue" name="vin"/>
            </div>
        </div>
        </div>
    </div>

<hr style="height:2px;background-color:lightslategray">

      <div class="container">
        <div class="row" @click="toggle2">
          <div class="col-8">
            <span class="dollar"><i class="fa fa-dollar "></i></span>
            <b>Review Payment Options</b><span>(Optional)</span>
          </div>
          <div class="col-4">
            <span v-if="!openAccordion">
              <i class="fas fa-angle-down"></i>
            </span>
            <span v-if="openAccordion">
              <i class="fas fa-angle-up"></i>
            </span>
          </div>
        </div>

        <div class="row mt-4" v-if="visible2">
          <div class="col-12">
              <p class="float-start">Select a Payment Option:</p>
          </div>
          <div class="row cash">
            <div class="col-12">
              <div id="cash-radio"><input type="radio" name="test_id" @change="onChange($event)" value="cash" />Cash</div>
            </div>
          </div>
        <div class="row finance mt-2">
          <div class="col-12">
            <div id="finance-radio"><input type="radio" name="test_id" @change="onChange($event)" value="finance" />Finance</div>
          </div>
        </div>
        <hr style="height:2px;background-color:lightslategray;margin-top:10px">
        <div class="row mt-3" v-if="finance">
          <div class="col-8 mb-2">
            <label class="float-start">How your Credit ? <span >*</span></label>
            <select id="t" class="form-select">
              <option>Select Credit</option>
              <option>Good</option>
              <option>Excellent</option>
              <option>Fair</option>
              <option>Repairing</option>
            </select>
          </div>
            
          <div class="text-start col-12 mt-3">
            <strong><b>Estimated Monthly Payment</b></strong>
          </div>
          <hr style="height:2px;background-color:lightslategray;margin-top:10px">
          <div class="row mt-3">
            <div class="col-2">
              <label>Down Payment </label>
            </div>
            <div class="col-4">
              <input type="text" v-model="sliderValue1" label="Down Payment"/>
            </div>
            <div class="col-2">
              <label>Term (months)</label>
            </div>
            <div class="col-4">
              <input type="text" v-model="sliderValue2" label="Terms (month)"/>
            </div>
          </div>
          <div class="row">
            <div id="t2" class="col-6">
              <input
                type="range"
                min="0"
                max="1000"
                v-model="sliderValue1"
                class="slider"
                step="100"
              />
            </div>
            <div id="t2" class="col-6">
              <input
                type="range"
                min=""
                max="1000"
                v-model="sliderValue2"
                class="slider"
                step="100"
              />
            </div>
          </div>
        </div>
      </div>
    </div>

<hr style="height:2px;background-color:lightslategray">

      <div class="container mt-3">
          <div class="row" @click="toggle3">
            <div class="col-8">
              <span class="motor"><i class='far fa-edit'></i></span>
              <b>Message Dealer</b> <span> (Optional)</span>
            </div>
            <div class="col-4">
              <span class="angle" v-if="!openAccordion">
                <i class="fas fa-angle-down"></i>
              </span>
              <span v-if="openAccordion">
                <i class="fas fa-angle-up"></i>
              </span>
          </div>
        </div>
      </div>   
      <div class="panel--body mt-4" v-if="visible3">
            <label for="exampleFormControlTextarea1" class="form-label float-start">Add a short message to the dealer:</label>
            <textarea class="form-control" rows="6" v-model="value" @change="e=>handleField(e)" name="message" placeholder="Write here any thing you want to send to dealer"></textarea>
            <p class="flot-start">
                <small>
                    Stay Safe. Read more about avoiding scams and protecting your money. By using this site, you agree to our Terms of Use & our Privacy Policy.
                </small>
            </p>
      </div>
      <hr style="height:2px;background-color:lightslategray">
</template>


<script>
import InputField from './inputField.vue'   
import DropDown from './dropdown.vue'
// import Radio from './radio.vue'
export default {
    data(){
        return {
          finance: false,
          showTrade : false,
          openAccordion : false,
          yearsArr : [],
          condition:['Excellent','Good','Fair','Poor'],
          sliderValue1: 50,
          sliderValue2: 50,
          visible1: false,
          visible2: false,
          visible3: false,
        }
    },
    components: {
        InputField,
        DropDown,
        // Radio,
    },
    methods: {
        toggle1() {
          this.openAccordion = !this.openAccordion;
          this.visible1 = !this.visible1;
        },
        toggle2() {
          this.openAccordion = !this.openAccordion;
          this.visible2 = !this.visible2;
        },
        toggle3() {
          this.openAccordion = !this.openAccordion;
          this.visible3 = !this.visible3;
        },
        noTrade() {
          this.showTrade = false;
        },
        tradeIn() {
          this.showTrade = true;
        },
        getValue (value,name) {
          this.$emit('handleTrade',value,name)
        },
        handleField(e){
          this.$emit('handleTrade',e.target.value,e.target.name);
        },
        onChange(event) {
              var data = event.target.value;
              console.log(this.finance);
              this.finance = data;
              console.log(this.finance);
        }
    },
    created(){
      const year = new Date().getFullYear()
      this.yearsArr=Array.from({length: year - 1990}, (value, index) => 1991 + index);
    },
}
</script>

<style scoped>
/* .angle {
  padding-right: 14px;
}
.accordion-panel-message {
  padding-right: 310px;
}
.accordion-panel-payment {
  padding-right: 250px;
}
.accordion-panel-trade{
  padding-right: 300px;
} */
.motor {
  padding: 8px;
  font-size:20px;
  color:red;
  border: 1px solid red;
  margin-right: 10px;
  border-radius: 50%;
}
.dollar {
  padding: 8px 14px;
  font-size:20px;
  color:red;
  border: 1px solid red;
  margin-right: 10px;
  border-radius: 50%;
}
#cash-radio {
  padding-top: 15px;
  padding-right: 210px;
}

.finance {
  height: 60px;
  widows: 100%;
  border: cadetblue;
  border: 2px solid lightslategrey;
  border-radius: 5px;
}
.cash {
  height: 60px;
  widows: 100%;
  border: cadetblue;
  border: 2px solid lightslategrey;
  border-radius: 5px;
}
#finance-radio {
  padding-top: 15px;
  padding-right: 190px;
}
.no-trade-button {
    font-size: 15px;
    height: 50px;
    width: 142px;
    background: white;
    border: 1px solid #ccc;
    border-radius: 5px;
}
.yes-trade-button {
    font-size: 15px;
    height: 50px;
    width: 142px;
    background: white;
    border: 1px solid #ccc;
    border-radius: 5px;
}
    
#button-trade:focus {
    font-family: bold;
    background-color: rgb(230, 227, 227);
    border: 2px solid darkred;
    outline-style: solid;
    outline-color: red;
}
#t {
  width: 100%;
  height: 50px;

  padding-left: 5px;
  padding-right: 5px;
  padding-top: 15px;
  padding-bottom: 15px;
  border: 1px solid grey;

  border-radius: 5px;
}
#t2 {
  padding-top: 50px;
}

.slider {
  -webkit-appearance: none;
  width: 100%;
  height: 25px;
  background: #d3d3d3;
  outline: none;
  opacity: 200px;
  border-radius: 20px;
  -webkit-transition: 0.2s;
  transition: opacity 0.2s;
  cursor: pointer;
}
#a {
  color: red;
}

</style> 
