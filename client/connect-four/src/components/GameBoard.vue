<template>
    <div class="header">
        <h3>Connect Four</h3>
        <h4>Two Player</h4>
    </div>


    <div class="board">
        <section class="column" v-on:click="playChip">
            <section class="row" id="a1">1</section>
            <section class="row" id="a2">2</section>
            <section class="row" id="a3">3</section>
            <section class="row" id="a4">4</section>
            <section class="row" id="a5">5</section>
            <section class="row" id="a6">6</section>
        </section>
        <section class="column" v-on:click="playChip">
            <section class="row" id="b1">1</section>
            <section class="row" id="b2">2</section>
            <section class="row" id="b3">3</section>
            <section class="row" id="b4">4</section>
            <section class="row" id="b5">5</section>
            <section class="row" id="b6">6</section>
        </section>
        <section class="column">
            <section class="row" id="c1">1</section>
            <section class="row" id="c2">2</section>
            <section class="row" id="c3">3</section>
            <section class="row" id="c4">4</section>
            <section class="row" id="c5">5</section>
            <section class="row" id="c6">6</section>
        </section>
        <section class="column">
            <section class="row" id="d1">1</section>
            <section class="row" id="d2">2</section>
            <section class="row" id="d3">3</section>
            <section class="row" id="d4">4</section>
            <section class="row" id="d5">5</section>
            <section class="row" id="d6">6</section>
        </section>
        <section class="column">
            <section class="row" id="e1">1</section>
            <section class="row" id="e2">2</section>
            <section class="row" id="e3">3</section>
            <section class="row" id="e4">4</section>
            <section class="row" id="e5">5</section>
            <section class="row" id="e6">6</section>
        </section>
        <section class="column">
            <section class="row" id="f1">1</section>
            <section class="row" id="f2">2</section>
            <section class="row" id="f3">3</section>
            <section class="row" id="f4">4</section>
            <section class="row" id="f5">5</section>
            <section class="row" id="f6">6</section>
        </section>
        <section class="column">
            <section class="row" id="g1">1</section>
            <section class="row" id="g2">2</section>
            <section class="row" id="g3">3</section>
            <section class="row" id="g4">4</section>
            <section class="row" id="g5">5</section>
            <section class="row" id="g6">6</section>
        </section>

    </div>

</template>

<script>

export default {

    methods: {

        playChip() {

            alert("Click registered");

            if(!this.event.classlist.contains("red") && !this.event.classlist.contains("yellow")){
                this.event.classlist.add("");
            }

        }

    }

}


</script>

<style>

.board {
    display: flex;

    flex-direction: row;
   
    height: fit-content;
    width: fit-content;
   
    border: 1px solid black;

    background-color: blue;
}

#a6 {
    background-color: red;
}

#a5 {
    background-color: yellow;
}

.column {
    display: flex;

    flex-direction: column;

    height: 100%;
    width: 100%;

    justify-content: space-evenly;

    margin: 15px;
        
}

.row {
    display: flex;
    flex-direction: row;
    height: 100px;
    width: 100px;
    border: 5px solid;

    justify-content: space-evenly;

    border-radius:50%;

    margin: 15px;

    background-color: white;
}

.square {
    grid-area: square;
    height: 100px;
    width: 100px;
    border: solid 1px black;
}


</style>