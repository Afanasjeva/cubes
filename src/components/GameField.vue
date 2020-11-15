<template>
  <div class="main">
    <section>
      <h1>Cubes</h1>
      <div class="panel">
        <button class="btn btn-primary btn-sm btn-block">{{ titles.start }}</button>
        <button class="btn btn-info btn-sm btn-block">{{ titles.newGame }}</button>
        <input id="points" type="text" class="" :value="game.points">
        <input id="time-left" type="text" class="" :value="game.timeLeft">
      </div>
    </section>
    <section>
      <ul>
        <li>Lorem ipsum dolor.</li>
        <li>Lorem ipsum dolor sit amet.</li>
      </ul>
    </section>
    <section class="field" v-if="initialized">
      <div class="grid">
        <div class="row" v-for="(row, index) in game.rows" :key="`row-${index}`">
          <div class="cell" v-for="(col, index) in game.cols" :key="`col-${index}`">
          </div>
        </div>
      </div>
    </section>
    <section>Result table</section>

  </div>
</template>

<script>
  export default {
    name: "GameField",
    data() {
      return {
        titles: {
          start: "Start",
          newGame: "New Game"
        },
        game: {
          colsN: 20,
          rowsN: 20,
          points: 0,
          timeLeft: 3600,
          cols: null,
          rows: null
        },
        initialized: false
      }
    },
    created() {
      this.game.cols = []
      this.game.rows = []
      for (let i = 0; i < this.game.colsN; i++) {
        this.game.cols.push(i)
        this.game.rows.push(i)
      }
      this.initialized = true
    }
  }
</script>

<style scoped lang="scss">
  .main {
    display: grid;
    grid-template-columns: 7fr 3fr;
    grid-template-rows: 1fr 9fr;
    width: 100vw;
    height: 100vh;
    position: fixed;
    left: 0;
    top: 0;
    overflow: hidden;
    padding: 24px;
    grid-column-gap: 24px;
    grid-row-gap: 24px;
    box-sizing: border-box;
    text-align: left;
  }

  section {
    border: 1px dotted gray;
    padding: 24px;
  }
  .panel {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .btn {
    width: 300px;
  }

  .field {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .grid {
    border: 1px solid green;
    box-sizing: border-box;
  }

  .row {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
  }

  .cell {
    margin: 0;
    padding: 0;
    font-size: 24px;
    display: block;
    height: 1em;
    width: 1em;
    box-sizing: border-box;
    border: 1px solid green;
  }
</style>
