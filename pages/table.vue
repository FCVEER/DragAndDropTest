<template>
  <div class="wrapper">
    <div class="table">
      <div class="column">
        <div class="header">
          <h1>
            Leverancier
          </h1>
        </div>
        <div class="dropZone"></div>
      </div>
      <div class="column">
        <div class="header">
          <h1>
            Artikel Groep
          </h1>
        </div>
        <div class="dropZone"></div>
      </div>
      <div class="column">
        <div class="header">
          <h1>
            Artikel Nummer
          </h1>
        </div>
        <div class="dropZone"></div>
      </div>
      <div class="column">
        <div class="header">
          <h1>
            Inclusief
          </h1>
        </div>
        <div class="dropZone"></div>
      </div>
      <div class="column">
        <div class="header">
          <h1>
            Exclusief
          </h1>
        </div>
        <div class="dropZone"></div>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .wrapper {
    width: 100vw;
    height: 100vh;
    background: whitesmoke;
  }

  .table {
    width: 90%;
    height: 90%;
    margin-left: 5%;
    margin-top: 2.5%;
    background: grey;
    display: inline-flex;
    flex-direction: row;
  }

  .table :first-child {
    border: none;
  }

  .column {
    height: 100%;
    width: 20%;
    background: blue;
    border-left: 1px red solid;
  }

  .header {
    background-color: red;
    padding: 5px;
    color: white;
  }

</style>

<script>
  export default {
    data() {
      return {
        items: [{
            id: 1,
            type: "Leverancier",
            payload: "L1"
          },
          {
            id: 2,
            type: "Leverancier",
            payload: "L2"
          },
          {
            id: 3,
            type: "Leverancier",
            payload: "L3"
          },
          {
            id: 4,
            type: "ArtGrp",
            payload: "100"
          },
          {
            id: 5,
            type: "ArtGrp",
            payload: "110"
          },
          {
            id: 6,
            type: "ArtGrp",
            payload: "120"
          },
        ]
      }
    }
  }
</script>
