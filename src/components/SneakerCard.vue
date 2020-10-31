<template>
    <div class="card" :style="{backgroundColor: bgColor}">
        <img class="shoe" alt="shoe" src="../assets/shoe-logo.png" v-if="!isDescription" @click="description">
        
        <div class="des" v-if="isDescription" @click="description">
            <b class="des-title">Sneaker {{color}}</b>
            <p class="des-text">This is the vesion {{color}} of the best brand of sneaker. Only 50$, just press the buy button and add it to cart.</p>
        </div>

        <h3 class="color" v-if="!isDescription">{{color}}</h3>
        <div class="container" :style="{backgroundColor: bgColor}">
            <button class="coin" @click="playAnimation">
                <h2 class="simbol" v-if="isDollar">$</h2>
                <h2 class="simbol" v-if="!isDollar">€</h2>
            </button>
            <button class="price">
                <b v-if="isDollar">50 $</b>
                <b v-if="!isDollar">43 €</b>
            </button>
            <button class="buy" :style="{color: bgColor}" @click="buySneaker()"><b>BUY</b></button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SneakerCard',
    props: {
        color: String,
        bgColor: String
    },
    data() {
        return {
            isDollar: true,
            isDescription: false
        };
    },   
    methods: {
        theFormat(number) {
            return number.toFixed(0);
        },
        playAnimation() {
            this.isDollar = !this.isDollar;
            if (this.isDollar){
                this.numberFrom = 50;
                this.numberTo = 43;
            }
            else{
                this.numberFrom = 43;
                this.numberTo = 50;
            }
            this.$refs.number2.play();
        },
        buySneaker() {
            this.$root.$emit('newBuy');
        },
        description() {
            this.isDescription = !this.isDescription;
        }
    }
}
</script>

<style scoped>
.card{
    background-color: #222A2C;
    width: 200px;
    border-radius: 30px;
    margin-top: 30px;
    transition: 0.3s;
    z-index: 1;
}


.shoe{
    width:100%;
    margin-top: 15px;
}

.des {
    width: 100%;
    height: 145px;
    text-align: center;
    text-decoration: none;
    font-family: Tahoma;
    font-size: 20px;
    color: white;
    padding-top: 15px;
}

.des-text {
    margin-top: 8px;
    text-decoration: none;
    font-family: Tahoma;
    font-size: 18px;

}

.container {
    background-color: #222A2C;
    height: 80px;
    border-bottom-left-radius: 30px;
    border-bottom-right-radius: 30px;
}

.coin{
    width: 38px;
    height: 38px;
    display: inline-block;
    border-radius: 50%;
    background-color: white;
    margin-top: 28px;
    margin-left: 13px;
    text-align: center;
    cursor: default;
    text-decoration: none;
    border: none;
}


button:focus {
    outline-style: none;
}

.simbol{
    margin: -2.5px 0px 0px 0px;
    color:  #222A2C;
    font-family: Tahoma;
    font-style: normal;
    font-size: 21px;
}

.price{
    background-color:white ;
    border: none;
    color:  #222A2C;
    text-align: center;
    text-decoration: none;
    font-family: Tahoma;
    font-style: normal;
    font-size: 14px;
    padding: 5px 15px 5px 15px;
    vertical-align:middle;
    border-radius: 12px;
    margin-left: 7px;
}

.bold {
  font-weight: bold;
  font-size: 14px;
}
.transition {
  transition: all 0.3s ease-in;
}

.buy{
    background-color:white ;
    border: none;
    color: #222A2C;
    text-align: center;
    text-decoration: none;
    font-family: Tahoma;
    font-style: normal;
    font-size: 14px;
    padding: 5px 15px 5px 15px;
    vertical-align:middle;
    border-radius: 12px;
    cursor: default;
    margin-left: 7px;
}


.color{
    margin: 0;
    text-align: center;
    color: white;
    font-family: Tahoma;
    font-style: normal;
    font-size: 20px;
}

</style>