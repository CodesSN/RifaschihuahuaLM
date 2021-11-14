<template>
    <div>
        <div id="counter">
            <div id="counter-container">
                <section class="text-3xl flex justify-center content-center flex-col mx-auto text-center"></section>
        <section class="flex text-6xl justify-content content-center"></section>
        
            </div>
        </div>

    </div>
</template>
<script>
var countDownDate = new Date("Feb 11, 2022 15:37:25").getTime();

var x = setInterval(function() {

  var now = new Date().getTime();

  var distance = countDownDate - now;

  var days = Math.floor(distance / (1000 * 60 * 60 * 24));
  var hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  var minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
  var seconds = Math.floor((distance % (1000 * 60)) / 1000);
 let rdays = `<div class="days mr-2 relative">
            <p>` + days + `</p>
            <p class="text-xs">Dias</p>
        </div>`;
    let rhours = `<div class="hours mr-2 relative">
                <p>` + hours + `</p>
                <p class="text-xs">Horas</p>
            </div>`;
    let rminutes = `<div class="minutes mr-2 relative">
                <p>` + minutes + `</p>
                <p class="text-xs">Minutos</p>
            </div>`;
    let rseconds = `<div class="seconds mr-2 relative">
                <p>` + seconds + `</p>
                <p class="text-xs">Segundos</p>
            </div>`;
  // Display the result in the element with id="demo"
  document.getElementById("counter-container").innerHTML = rdays + rhours
  + rminutes + rseconds;

  // If the count down is finished, write some text
  if (distance < 0) {
    clearInterval(x);
    document.getElementById("demo").innerHTML = "EXPIRED";
  }
}, 1000);


export default {
    data: () => ({
        displaydays: x.days,
        displayhours: x.hours,
        displayminutes: x.minutes,
    })
    }
</script>
<style>
#counter {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top:30px;
}
#counter-container {
    margin-top:60px;
    width: 60%;
    height: 60%;
    display: flex;
    justify-content: center;
    align-items: center;
    color: rgb(95, 95, 95)
}
.days {
    width: 120px;
    height: 30%;
    text-align: center;
    justify-content: center;
    align-items: center;
    background-color: rgb(255, 255, 255);
    font-size: 1rem;
    padding: 1rem;
    border-top-left-radius:10px;
    border-bottom-left-radius:10px;
}
.text-xs{
    margin-left:5px;
    margin-top:-20px;
}
.hours {
    width: 120px;
    height: 30%;
    text-align: center;
    justify-content: center;
    align-items: center;
    background-color: rgb(255, 255, 255);
    font-size: 1rem;
    padding: 1rem;
}
.minutes {
    width: 120px;
    height: 30%;
    text-align: center;
    justify-content: center;
    align-items: center;
    background-color: rgb(255, 255, 255);
    font-size: 1rem;
    padding: 1rem;
}
.seconds {
    width: 120px;
    height: 30%;
    text-align: center;
    justify-content: center;
    align-items: center;
    background-color: rgb(255, 255, 255);
    font-size: 1rem;
    padding: 1rem;
    border-top-right-radius:10px;
    border-bottom-right-radius:10px;
}
@media screen and (max-width: 950px) {
    #counter-container {
    margin-top:0px;
    width: 60%;
    height: 60%;
    display: flex;
    justify-content: center;
    align-items: center;
    color: rgb(95, 95, 95)
}
   .days {
    width: 90px;
    height: 90px;
    text-align: center;
    justify-content: center;
    align-items: center;
    background-color: rgb(255, 255, 255);
    font-size: .8rem;
    padding: .8rem;
    border-top-left-radius:10px;
    border-bottom-left-radius:10px;
}
.text-xs{
    margin-left:5px;
    margin-top:-2px;
}
.hours {
    width: 90px;
    height: 90px;
    text-align: center;
    justify-content: center;
    align-items: center;
    background-color: rgb(255, 255, 255);
    font-size: .8rem;
    padding: .8rem;
}
.minutes {
    width: 90px;
    height: 90px;
    text-align: center;
    justify-content: center;
    align-items: center;
    background-color: rgb(255, 255, 255);
    font-size: .8rem;
    padding: .8rem;
}
.seconds {
    width: 90px;
    height: 90px;
    text-align: center;
    justify-content: center;
    align-items: center;
    background-color: rgb(255, 255, 255);
    font-size: .8rem;
    padding: .8rem;
    border-top-right-radius:10px;
    border-bottom-right-radius:10px;
}
}
</style>