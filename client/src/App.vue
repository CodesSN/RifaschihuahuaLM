<template>
  <div id="app">
    <div id="header">
      <div id="main-container">
        <div id="logo">
          <a href="#banner"><img src="./assets/logo.jpeg" alt="Logo"></a>
          <p>Rifas chihuahua LM</p>
        </div>
        <div id="nav-container">
          <nav>
            <ul>
              <a href="#tickets"><li><span class="fas fa-home"></span> Comprar</li></a>
              <a href=""><li><span class="icon-about"></span> About</li></a>
              <a href="https://api.whatsapp.com/send?phone=526144705903"><li><span class="icon-contact"></span> Contact</li></a>
            </ul>
          </nav>
        </div>
      </div>
    </div>
    <div id="banner">
      <div id="banner-content">
          <div id="banner-description">
            <div id="cardes">
              <img id="i1" src="./assets/bannerinf.png" alt="">
              <img id="i2" src="./assets/bannerinfocel.png" alt="">
            </div>
            <Counter/>
          </div>
      </div>
      </div>
      <div id="info">
        <div id="info-container">
          <img id="p1" src="./assets/participa.png" alt="" width="1450px">
          <img id="p2" src="./assets/participacel.png" alt="" width="1450px">
        </div>
      </div>
      <div id="tickets">
        <div id="tickets-container">
          <div id="tdis">
          <img id="t1" src="./assets/tdis.png" alt="" >
          <img id="t2" src="./assets/tdiscel.png" alt="" >
        </div>
        <Tickets/>
        </div>
      </div>
  </div>
</template>

<script>
import Tickets from './components/tickets.vue';
import Counter from './components/countdown.vue';
export default {
  name: 'App',
  components: {
    Counter,
    Tickets
  },
  data(){
    return {
  }
}
}
</script>

<style>
*{
  box-sizing: border-box;
}
body{
  overflow-x: hidden;
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
}
a{
  text-decoration: none;
}
#header{
  margin-top:-4px;
  position: fixed;
  background-color: #ffffff;
  height: 80px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 0 10px 1px rgba(167, 167, 167, 0.118);
  z-index: 1;
}
#main-container{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  height: 100px;
}
#nav-container{
  display: flex;
  justify-content: space-between;
  align-items: center;
}
#logo{
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 10%;
}
#logo img{
  width: 120px;
}
nav{
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-right: 150px;
}
nav ul{
  display: flex;
  justify-content: space-between;
  align-items: center;
}
nav ul li{
  list-style: none;
  color: rgb(17, 17, 17);
  text-align: center;
  width: 120px;
  margin: 2px;
}
nav ul a li{
  text-decoration: none;
  color: rgb(17, 17, 17);
}
h2{
  padding: 0 10px;
}
#banner{
  color: #ffffff;
  margin-top:2px;
  background-image: url("./assets/b1.jpeg");
  background-attachment: fixed;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 850px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
#banner-content{
  background-color: rgba(4, 4, 4, 0.248);
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
#banner-description{
  margin-top: -20px;
  width: 100%;
  height: 40%;
  text-align: left;
  justify-content: left;
  align-items: center;
}
#banner-description img{
  width: 100%;
}
#cardes{
  text-shadow:0px 0px 10px #00000074;
  position: relative;
  margin-top: -30px;
  display: flex;
  width: 100%;
  height: 100%;
  text-align: center;
  justify-content: center;
  align-items: center;
  margin-bottom:50px;
}
#cardes #i1{
  width: 540px;
  max-width: 100%;  
}
#cardes #i2{
  display: none;
}
#infocar h1{
  font-size: 70px;
  font-weight: bold;
  margin-bottom: -32px;
}
#infocar h2{
  font-size: 50px;
  font-weight: bold;
  margin-bottom: 2px;
}
#infocar h3{
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 2px;
}
#infocar h4{
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 2px;
}
#info{
  background-color: #315DCC;
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
#info-container{
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
#info-container #p1{
  max-width: 100%;
}
#info-container #p2{
  display: none;
}
#tickets{
  background-color: #ffffff;
  height: 100%;
  width: 100%;
  justify-content: center;
  align-items: center;
}
#tickets-container{
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
#tdis{
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
}
#tdis #t1{
  margin-top: 100px;
  width: 980px;
  max-width:90%;
}
#tdis #t2{
  display: none;
}
@media screen and (max-width: 768px){
  #header{
    height: 60px;
  }
  #logo{
    margin-left: 0;
    margin-top: 10px;
  }
  #logo p{
    font-size: 10px;
  }
  #logo img{
    width: 60px;
  }
  #nav-container{
    margin-right: 0;
  }
  nav ul li{
  list-style: none;
  color: rgb(17, 17, 17);
  text-align: center;
  width: 70px;
  margin: -2px;
}
  #banner{
    height: 550px;
  }
#banner-description img{
  width: 90%;
}
  #cardes{
    margin-left: 0;
  }
  #cardes #i1{
    display: none;
}
#cardes #i2{
  display: flex;
  max-width: 100%; 
}
#info-container #p1{
  display: none;
}
#info-container #p2{
  max-width: 100%;
  display: flex;
}
#tdis #t1{
  display: none;
}
#tdis #t2{
  display: block;
  margin-top: 80px;
  width: 980px;
  max-width:90%;
}
}
</style>
