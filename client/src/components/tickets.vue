<template>
  <div>
      <div id="container">
          <div id="search">
                <div class="search-box">
                    <input placeholder="numero de ticket" v-model="search" type="text" v-on:change="filterTickets">
                    <button class="search-btn" v-on:click="filterTickets"><p>Buscar</p></button>
                </div>
          </div>
      </div>
      <div id="container">
          <div id="row">
              <div id="col" v-for="ticket in tickets" :key="ticket._id">
                  <a href="#reservar" v-on:click="reservar = ticket.id" v-if="ticket.reserved == false" :key="ticket.reserved">
                 <div id="card">
                          <p id="id">
                          {{ ticket.id}}
                      </p>
                  </div>
                  </a>
                   <a v-else>
                  <div id="card-false">
                          <p id="id">
                          {{ ticket.id}}
                      </p>
                  </div>
                  </a>
              </div>
          </div>
      </div>
      <div id="reservar">
          <div id="container">
              <div id="infores">
                                <p>Numero de Boleto : {{(reservar != "")? reservar : "No Has Seleccionado Un Numero"}}</p>
                            <h1>¡¡Importante el correo de reservacion puede estar en la parte de spam de su correo!!</h1>
                            </div>
                  <form>
                        <input type="email" name="email" v-model="email" placeholder="email" required>
                        <input type="text" name="name" v-model="name" placeholder="nombre" required>
                        <input type="text" name="lastname" v-model="lastname" placeholder="apellido" required>
                        <input type="text" name="phone" v-model="phone" placeholder="telefono" required>
                        <input type="text" name="state" v-model="state" placeholder="estado" required>
                        <input type="text" name="city" v-model="city" placeholder="ciudad" required>
                        <a href="#tickets"><button id="btn-reservar" v-on:click="reservarTicket">Reservar</button></a>
                  </form>
          </div>
      </div>
      <div id="footer">
                      <div id="container">
              <div id="footer-content">
                  <div id="footer-logo">
                      <img src="img/logo.png" alt="">
                  </div>
                  <div id="footer-info">
                      <p>
                          <span>Rifas chihuahua LM . </span>
                          <span>chihuahua chihuahua . 2021 .</span>
                      </p>
                      <p>
                          <span>Telefono: </span>
                          <span>(+52) 1 614 199 1693</span>
                      </p>
                      <p>
                          <span>Email: </span>
                          <span>enrique.miranda78@hotmail.com</span>
                        </p>
                        <p>
                          <span>Creada por: </span>
                          <span>Raul Hibran Acosta Piñon</span>
                        </p>
                  </div>
              </div>
           </div>
      </div>
      </div>
</template>

<script>
import vue from 'vue'
import axios from 'axios';
import vueAxios from 'vue-axios';

vue.use(vueAxios, axios);



export default {
    data() {
        return {
            tickets: [],
            baseUrl: 'http://localhost:3000/',
            search: '',
            reservar: '',
            email: '',
            phone: '',
            name: '',
            lastname: '',
            state:"",
            city:""
        }
    },
    created() {
        this.getTickets();
    },
    methods: {
        getTickets() {
            const params = {
                id: (this.search) ? this.search : 0
            }
            axios.get(this.baseUrl+ "found/" + params.id)
                .then(response => {
                    this.tickets = response.data.data;
                    console.log(response.data.data);
                })
        },
        getTicketsPR() {
            const params = {
                id: 0
            }
            axios.get(this.baseUrl+ "found/" + params.id)
                .then(response => {
                    this.tickets = response.data.data;
                    console.log(response.data.data);
                })
                .catch(error => {
                    console.log(error);
                })
        },
        filterTickets() {
           this.getTickets();
        },
        reservarTicket() {
            const params = {
                id: this.reservar,
                email: this.email,
                phone: this.phone,
                name: this.name,
                lastname: this.lastname,
                state: this.state,
                city: this.city
            }
            axios.put(this.baseUrl + "reservar/" + params.id + "/" + params.email +  "/" + params.name + "/" + params.lastname + "/" + params.phone + "/" + params.state + "/" + params.city)
                .then(() => {
                    this.getTicketsPR();
                })
                .catch(error => {
                    console.log(error);
                })
        }
    },
}
</script>
<style>
#container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  border-radius: 10px;
}
#row {
    margin:50px;
  display: flex;
  width:70%;
  max-width: 1200px;
  flex-wrap: wrap;
  justify-content: center;
  border-radius: 10px;
}
#col {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  border-radius: 10px;
  margin:5px;
}
#card {
  display: flex;
  width: 100px;
  height: 45px;
  flex-wrap: wrap;
  justify-content: center;
  border: 2px solid rgb(158, 158, 158);
  color:rgb(100, 100, 100);
  border-radius: 100px;
}
#card-false{
  display: flex;
  width: 100px;
  height: 45px;
  flex-wrap: wrap;
  justify-content: center;
  background-color: rgb(55, 55, 55);
  color: white;
  border-radius: 100px;
}
#id {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
#search {
    margin-top:50px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.search-box {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.search-btn {
  display: flex;
  width: 120px;
  height: 40px;
  flex-wrap: wrap;
  justify-content: center;
  background-color: #315DCC;
  border: none;
  color: white;
  border-top-right-radius:100px;
  border-bottom-right-radius:100px;
}
#search input {
    outline: none;
    padding-left:50px;
    display: flex;
    width: 320px;
    height: 40px;
    flex-wrap: wrap;
    border: none;
    justify-content: center;
    background-color: rgb(242, 242, 242);
    color: rgb(97, 97, 97);
    border-top-left-radius:100px;
  border-bottom-left-radius:100px;
}
#reservar {
    width: 100%;
    color: white;
    background-color: #315DCC;
    margin-top:50px;
    padding-bottom: 50px;
    text-align: center;
  justify-content: center;
}
#infores{
    width:100%;
    height: 120px;
    margin-top:50px;
    margin-bottom:20px;
    text-align: center;
    justify-content: center;
}
#infores h1{
    color:white;
    font-size:25px;
    width:600px;
    max-width:100%;
    margin: auto;
}
#infores p{
    font-size:20px;
}

#reservar input {
    outline: none;
    padding-left:50px;
    background-color: rgb(242, 242, 242);
    display: flex;
    width: 320px;
    color: #315DCC;
    height: 40px;
    margin-top:7px;
    border: none;
    outline: none;
    border-radius:100px;
    }
#btn-reservar {
    margin:20px;
    width: 220px;
    height: 45px;
    background-color: #ffffff;
    text-align: center;
    justify-content: center;
    border: none;
    color: #315DCC;
    border-radius:70px;
}
#btn-reservar p {
    background-color: #315DCC;
    font-size:16px;
}
#footer {
    margin: 0;
    width:100%;
    height:200px;
    background-color: #ffffff;
    color: #315DCC;
    text-align: center;
    justify-content: center;
    margin: auto;
}

@media screen and (max-width: 768px){
    #container {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        border-radius: 10px;
    }
    #row {
        margin:50px;
        display: flex;
        width:100%;
        max-width: 1200px;
        flex-wrap: wrap;
        justify-content: center;
        border-radius: 10px;
    }
    #col {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        border-radius: 10px;
        margin:5px;
    }
    #card {
        display: flex;
        width: 100px;
        height: 45px;
        flex-wrap: wrap;
        justify-content: center;
        border: 2px solid rgb(55, 55, 55);
        border-radius: 100px;
    }
    #card-false{
        display: flex;
        width: 100px;
        height: 45px;
        flex-wrap: wrap;
        justify-content: center;
        background-color: rgb(55, 55, 55);
        color: white;
        border-radius: 100px;
    }
    #id {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
    #search {
        margin-top:50px;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
    .search-box {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
    .search-btn {
        display: flex;
        width: 100px;
        height: 40px;
        flex-wrap: wrap;
        justify-content: center;
        background-color: #315DCC;
    }
    #infores{
        margin-bottom:80px;
    }
    #search input {
    padding-left:50px;
    width: 220px;
    height: 40px;
}
#footer {
    margin: 0;
    width:100%;
    height:200px;
    background-color: #ffffff;
    color: #315DCC;
    text-align: center;
    justify-content: center;
    margin: auto;
}
#footer p{
    font-size:14px;
}
}
</style>