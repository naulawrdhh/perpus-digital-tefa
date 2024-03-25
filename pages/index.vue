<template>
    <div class="container-fluid">
      <div class="row my-5">
        <div class="col-lg-6">
          <nuxt-link to="/pengunjung/tambah">
            <div class="card bg-pengunjung rounded-5">
              <div class="card-body  ">
                <h2>Pengunjung</h2>
              </div>
            </div>
          </nuxt-link>
        </div>
  
        <div class="col-lg-6">
          <nuxt-link to="/buku">
            <div class="card bg-buku rounded-5">
              <div class="card-body">
                <h2>Cari Buku</h2>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>
    <div class="statistik">
      <h1>STATISTIK</h1>
    </div>

    <div class="container-fluid">
    <div class="row my-5 d-flex justify-content-around-5 ">
      <div class="col-lg-6 ">
          <div class="card rounded-5 color1">
            <div class="card-body d-flex justify-content-around d-flex align-items-center">
              <h2 class="text"><span class="no">3</span>pengunjung</h2>
              </div>
            </div>
        </div>
        <div class="col-lg-6">
          
            <div class="card rounded-5 color2">
              <div class="card-body d-flex justify-content-around d-flex align-items-center">
                <h2 class="text"><span class="no">140</span> Buku</h2>
              </div>
            </div>
        </div>
      </div>
    </div>
  </template>
  
  
  <style scoped>
  .no{
    font-size: 67px;
  }
  .color1{
    background-color:#FDF6D3;
  }
  .color2{
    background-color: #E2DDFF;
  }
  .text{
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .card {
    height: 250px;
    box-shadow: 1px 1px 10px #424242;
  }
  .card.bg-pengunjung {
    background-image: url('../assets/img/perpus.jpg');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
  }
  .card.bg-buku {
    background: url('../assets/img/buku.jpeg') no-repeat center center;
    background-size: cover;
  }
  </style>