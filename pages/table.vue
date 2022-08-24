<template>
  <div class="wrapper">
    <div class="table">
      <div class="column" id="first">
        <div class="header" id="firstHeader">
          <h1>
            Leverancier
          </h1>
        </div>
        <div class="dropZone" @drop="onDrop($event,Leverancier)" @dragover.prevent @dragenter.prevent>
          <div class="dragElement" v-for="item in Leverancier" :key="item.id" draggable
            @dragstart="startDrag($event, Leveranciers)">
            {{item.payload}}
          </div>
        </div>
      </div>
      <div class="column">
        <div class="header">
          <h1>
            Artikel Groep
          </h1>
        </div>
        <div class="dropZone">
          <div class="dragElement" v-for="item in ArtGrp" :key="item.id" draggable
            @dragstart="startDrag($event, ArtGrp)">
            {{item.payload}}
          </div>

        </div>
      </div>
      <div class="column">
        <div class="header">
          <h1>
            Artikel Nummer
          </h1>
        </div>
        <div class="dropZone">
          <div class="dragElement" v-for="item in ArtNr" :key="item.id" draggable
            @dragstart="startDrag($event, ArtNr)">
            {{item.payload}}
          </div>

        </div>
      </div>
      <div class="column">
        <div class="header">
          <h1>
            Inclusief
          </h1>
        </div>
        <div class="dropZone"></div>
      </div>
      <div class="column" id="last">
        <div class="header" id="lastHeader">
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
    background: blue;
  }

  .table {
    width: 90%;
    height: 90%;
    margin-left: 5%;
    margin-top: 2.5%;
    display: inline-flex;
    flex-direction: row;
    box-shadow: 2px 2px 2px gray;
  }

  #first {
    border-radius: 5px 0 0 5px;
    border-left: none;
  }

  #firstHeader {
    border-radius: 5px 0 0 0;
  }

  #last {
    border-radius: 0 5px 5px 0;
  }

  #lastHeader {
    border-radius: 0 5px 0 0;
  }

  .column {
    height: 100%;
    width: 20%;
    background-color: aliceblue;
    border-left: 1px gray solid;
  }

  .header {
    background-color: gray;
    padding: 5px;
    text-align: center;
  }

  .dragElement {
    background-color: gray;
    width: 90%;
    height: 1rem;
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
    },
    computed: {
      Leverancier() {
        return this.items.filter((item) => item.type === "Leverancier")
      },
      ArtGrp() {
        return this.items.filter((item) => item.type === "ArtGrp")
      },
      ArtNr() {
        return this.items.filter((item) => item.type === "ArtNr")
      },
    },
    methods: {
      startDrag(evt, item) {
        evt.dataTransfer.dropEffect = 'move'
        evt.dataTransfer.effectAllowed = 'move'
        evt.dataTransfer.setData('itemID', item.id)
      },
      onDrop(evt, list) {
        const itemID = evt.dataTransfer.getData('itemID')
        const item = this.items.find((item) => item.id == itemID)
        item.list = list
      }
    }
  }

</script>
