<template>
  <div class="wrap">

    <div class="col">
      <span>Цельсий</span>
      <input placeholder="0" v-model.number="C" @click="active = 'C'" @keyup="convert">
      <p>F = (C * 1.8) + 32</p>
      <p>K = C + 273.15</p>
    </div>

    <div class="col">
      <span>Фаренгейт</span>
      <input placeholder="0" v-model.number="F" @click="active = 'F'" @keyup="convert">
      <p>C = (F -32) / 1.8</p>
      <p>K = ((F - 32) / 1.8) + 273.15</p>
    </div>

    <div class="col">
      <span>Кельвин</span>
      <input placeholder="0" v-model.number="K" @click="active = 'K'" @keyup="convert">
      <p>C = K - 273.15</p>
      <p>F = ((K - 273.15) * 1.8) + 32</p>
    </div>

  </div>
</template>

<script>
  export default {
    data: () => ({
      C: 0,
      F: 0,
      K: 0,
      active: null
    }),
    methods: {
      convert(){
        switch (this.active) {
          case "C":
            this.F = (this.C * 1.8) + 32
            this.K = this.C + 273.15
            console.log("C")
            break
          case "F":
            this.C = (this.F -32) / 1.8
            this.K = ((this.F - 32) / 1.8) + 273.15
            console.log("F")
            break
          case "K":
            this.C = this.K - 273.15
            this.F = ((this.K - 273.15) * 1.8) + 32
            console.log("K")
            break
        }
        this.C.toFixed(2)
        this.F.toFixed(2)
        this.K.toFixed(2)
      },
    }
  }
</script>

<style>
  body{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    font-family: sans-serif;
    color: #444;
  }
  .wrap{
    max-width: 700px;
    margin: 0 auto;
    display: flex;
    justify-content: space-around;
  }
  .col input{
    margin-top: 7px;
  }
  .col span{
    font-weight: 600;
  }
  .col p{
    font-size: 12px;
    color: #666;
  }

</style>