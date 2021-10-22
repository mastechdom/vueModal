<template>
    <div class="container ex2">
        <!-- <p class="float-start">Hi Azhar ths is your result page</p><br /> -->
        <div class="row">
            <div class="col-8 text-start"><strong>First Name : </strong>{{items.fname}} </div>
            <div class="col-8 text-start"><strong>Last Name : </strong>{{items.lname}} </div>
            <div class="col-8 text-start"><strong>Email : </strong>{{items.email}} </div>
            <div class="col-8 text-start"><strong>Mobile : </strong>{{items.mobile}} </div>
            <div class="col-8 text-start"><strong>My Offer : </strong>{{items.myOffer}}</div>
            <div class="col-8 text-start"><strong>Years : </strong>{{tradeItems.years}} </div>
            <div class="col-8 text-start"><strong>Make : </strong>{{tradeItems.make}} </div>
            <div class="col-8 text-start"><strong>Model : </strong>{{tradeItems.model}} </div>
            <div class="col-8 text-start"><strong>Condition : </strong>{{tradeItems.condition}} </div>
            <div class="col-8 text-start"><strong>Milage : </strong>{{tradeItems.milage}}</div>
            <div class="col-8 text-start"><strong>VIN : </strong>{{tradeItems.vin}}</div>
            <div class="col-8 text-start"><strong>Message : </strong>{{tradeItems.message}}</div>
        </div>
    </div>
    <div class="footer">
        <hr style="width:95%;text-align:center;background-color:lightslategray">
        <button class="close" @click="closeModal()">Close</button>
    </div>
</template>

<script>

export default {
    props: ['items','tradeItems'],
    methods: {
        closeModal() {
            this.$emit('close-modal');
        }
    },
}
</script>

<style scoped>
#heading-result {
    padding-left: 15px;
}
.footer {
    background-color: white;
    position: relative;
}
.close {
    font-size: 20px;
    height: 50px;
    width: 300px;
    color: white;
    background: darkslategrey;
    border-radius: 5px;
}
.ex2 {
    padding-left: 30px;
    padding-right: 30px;
    width: 100%;
    height: 350px;
    overflow: scroll;
}
</style>
