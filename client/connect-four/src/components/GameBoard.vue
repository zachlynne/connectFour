<template>
    <div class="header">
        <h3>Connect Four</h3>
        <h4  v-bind:style="{ color: currentPlayer === 'red' ? 'red' : 'yellow' }">It's {{ currentPlayer }}'s turn!</h4>
    </div>


    <div class="board">
        <!-- This creates the elements in the board by section -->
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
        <section class="column" v-on:click="playChip">
            <section class="row" id="c1">1</section>
            <section class="row" id="c2">2</section>
            <section class="row" id="c3">3</section>
            <section class="row" id="c4">4</section>
            <section class="row" id="c5">5</section>
            <section class="row" id="c6">6</section>
        </section>
        <section class="column" v-on:click="playChip">
            <section class="row" id="d1">1</section>
            <section class="row" id="d2">2</section>
            <section class="row" id="d3">3</section>
            <section class="row" id="d4">4</section>
            <section class="row" id="d5">5</section>
            <section class="row" id="d6">6</section>
        </section>
        <section class="column" v-on:click="playChip">
            <section class="row" id="e1">1</section>
            <section class="row" id="e2">2</section>
            <section class="row" id="e3">3</section>
            <section class="row" id="e4">4</section>
            <section class="row" id="e5">5</section>
            <section class="row" id="e6">6</section>
        </section>
        <section class="column" v-on:click="playChip">
            <section class="row" id="f1">1</section>
            <section class="row" id="f2">2</section>
            <section class="row" id="f3">3</section>
            <section class="row" id="f4">4</section>
            <section class="row" id="f5">5</section>
            <section class="row" id="f6">6</section>
        </section>
        <section class="column" v-on:click="playChip">
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

    data() {
        return {
            currentPlayer: "red", // red goes first
        }
    },

    methods: {

        playChip(event) // function to play a chip
        {

            const elementId = event.target; // get the element that was clicked

            if (!elementId.classList.contains("red") && !elementId.classList.contains("yellow")) // if the element does not have a color, cannot overwrite other play's chip
            {
                elementId.classList.add(this.currentPlayer); // add the current player's color to the element
                this.currentPlayer = this.currentPlayer === "red" ? "yellow" : "red"; // switch players
            }

            //need to create a function to check for win conditions
            //need to create a function to check for a tie
            //need to create a function to reset the board
            //need to fix an issue where column is changing color on click, this is also counting as a player's turn


        },

    }

}


</script>

<style>
/* Style for the board */
.board {
    display: flex;

    flex-direction: row;

    height: fit-content;
    width: fit-content;

    border: 1px solid black;

    background-color: blue;


}


/* Style for each of the columns on the board */
.column {
    display: flex;

    flex-direction: column;

    height: 100%;
    width: 100%;

    justify-content: space-evenly;

    margin: 15px;

}

/* Style for each of the rows on the board, with access to each piece in that row */
.row {
    display: flex;
    flex-direction: row;
    height: 100px;
    width: 100px;
    border: 5px solid;

    justify-content: space-evenly;

    border-radius: 50%;

    margin: 15px;

    background-color: white;
}

/* Style for red player */
.red {
    background-color: red;
}

/* Style for yellow player */
.yellow {
    background-color: yellow;
}

.blue {
    background-color: blue;
}

/* Style for pieces to be circles and in grid area */
.square {
    grid-area: square;
    height: 100px;
    width: 100px;
    border: solid 1px black;
}

h3 {
    text-align: center;
    font-size: 2em;
}

h4 {
    text-align: center;
    font-size: 1.5em;
}
</style>