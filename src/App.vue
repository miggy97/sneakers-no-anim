<template>
  <div id="app">
    
    <NavBar/>
    <div style="height: 100px"></div>
      
    <div :class="[{'cards':!isMobile}, {'smallCard': isMobile}]">
      <SneakerCard color="black" bgColor="#222A2C"/>
      <SneakerCard color="yellow" bgColor="#D6BE4A"/>
      <SneakerCard color="blue" bgColor="#557CE2"/>
      <SneakerCard color="pink" bgColor="#ED5ECD"/>
    </div>
    
    <div class="vec">
      <div :class="[{'cards':!isMobile}, {'smallCard': isMobile}]">
        <SneakerCard color="green" bgColor="#00BF97"/>
        <SneakerCard color="red" bgColor="#D16F51"/>
        <SneakerCard color="purple" bgColor="#8E60B4"/>
        <SneakerCard color="pink" bgColor="#B6804C"/>
      </div> 
    </div>
    <div class="bg-bottom1"></div>
    <img id="checkout" class="vec-pay" src="./assets/vec-pay.svg">
    <h1 class="checkout">CHECKOUT</h1>
    <PayCard/>
    <img class="vec-bottom" src="./assets/vec-bottom.svg">
  </div>
</template>

<script>
import NavBar from './components/NavBar'
import SneakerCard from './components/SneakerCard'
import PayCard from './components/PayCard'

export default {
  name: 'App',
  components: {
    NavBar,
    SneakerCard,
    PayCard
  },
  data:( ) => {
    return {
      isMobile: false
    }
  },
  methods: {
    handleView(){
      this.isMobile = window.innerWidth <= 420;
    }
  },
  mounted() {
    window.addEventListener('resize', () => {
        this.handleView();
    });  
  },
  created() {
    this.handleView();
  },
}
</script>

<style>

*{
  margin: 0;
}

#app {
  font-family: Tahoma,Verdana,Segoe,sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.cards{
  display: flex;
  flex-wrap: wrap;
  justify-content:space-evenly;
  margin-left: 100px;
  margin-right: 100px;
}

.smallCard{
  display: flex;
  flex-wrap: wrap;
  justify-content:space-evenly;
  margin-left: 15px;
  margin-right: 15px;
}

.particles {
  position: absolute;
  width: 100%;
  height:65%;
}

.vec{
  background-image: linear-gradient(to top, #359fe7, #2299ef, #1b91f6, #2989fb, #3f7ffe, #4a79ff, #5672ff, #626bff, #6467ff, #6762ff, #6a5eff, #6d59ff);
  margin-top: 20px;
  border-top-left-radius: 40px;
  transform: skewY(-2deg);
  z-index: -1;
}

.vec::before {
  content: "";
  width: 40px;
  height: 40px;
  background-color: #6D59FF;
  position:absolute;
  top: -39px;
  right: 0;
  z-index: -3;
}

.vec::after {
  content: "";
  width: 80px;
  height: 80px;
  background-color: white;
  top: -80px;
  position:absolute;
  right: 0;
  border-radius: 50%;
  z-index: -2;
}

.vec .cards{
  transform: skewY(2deg);
}

.bg-bottom1 {
  background-color: #359FE7;
  width: 100%;
  height: 150px;
  margin-top: -50px;
}

.vec-pay {
  width: 50%;
  position:absolute;
  float:right;
  right: 0;
}

.vec-bottom {
  width: 50%;
  position: absolute;
  z-index: -1;
}

.checkout {
  font-family: Tahoma;
  font-style: normal;
  font-weight: bold;
  font-size: 20px;
  line-height: 43px;
  color: #6D59FF;
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  margin-top: 100px;
}
</style>
