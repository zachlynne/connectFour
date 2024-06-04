<template>
    <div class="header">
        <h3>Connect Four</h3>
        <h4>Two Player</h4>
    </div>

    <div class="board">
        <section class="square" id="squareone">1</section>
        <section class="square" id="square2">2</section>
        <section class="square" id="square3">3</section>
        <section class="square" id="square4">4</section>
        <section class="square" id="square5">5</section>
        <section class="square" id="square6">6</section>
        <section class="square" id="square7">7</section>

    </div>

</template>

<script>

</script>

<style>

.board {
    display: grid;
   
    height: 600px;
    width: 700px;

    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr;

    gap: 5px;
    border: 2px solid black;

    background-color: yellow;

   
}

.square {
    grid-area: square;
    height: 100px;
    width: 100px;
    border: solid 1px black;
}

</style>