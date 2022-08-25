<template>
  <div class="wrapper">
    <div class="table">
      <div class="column" id="first">
        <div class="header" id="firstHeader">
          <h1>
            Leverancier
          </h1>
        </div>
        <div class="dropZone" @drop="onDrop($event,'Leverancier')" @dragover.prevent @dragenter.prevent>
          <div class="dragElement" v-for="item in Leverancier" :key="item" draggable
            @dragstart="startDrag($event, item)">
            <p style="text-align:center">{{item.payload}}</p>
          </div>
        </div>
      </div>
      <div class="column">
        <div class="header">
          <h1>
            Artikel Groep
          </h1>
        </div>
        <div class="dropZone"  @drop="onDrop($event,'ArtGrp')" @dragover.prevent @dragenter.prevent>
          <div class="dragElement" @drop="onDrop($event, 'ArtGrp')" v-for="item in ArtGrp" :key="item.id" draggable
            @dragstart="startDrag($event, item)">
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
        <div class="dropZone"  @drop="onDrop($event,'ArtNr')" @dragover.prevent @dragenter.prevent>
          <div class="dragElement" v-for="item in ArtNr" :key="item.id" draggable
            @dragstart="startDrag($event, item)">
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
  .dropZone{
    width: 100%;
    height: 90%;
    overflow-y: auto;
    
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
    height: 10%;
  }

  .dragElement {
    background-color: rgba(78, 72, 72, 0.1);
    border-radius: 5px;

    width: 90%;
    height: 15%;
    margin: 5%;
    display: flex;
    justify-content: center;
    align-items: center;
}

</style>

<script>
  export default {
    data() {
      return {
        items: [
          {
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
          {
            id: 7,
            type: "ArtNr",
            payload: "100"
          },
          {
            id: 8,
            type: "ArtNr",
            payload: "110"
          },
          {
            id: 9,
            type: "ArtNr",
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
        console.log(list);
        item.type = list
      }
    }
  }
</script>
