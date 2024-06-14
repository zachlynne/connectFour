<template>
    <div class="header">
        <h3>Connect Four</h3>
        <h4 v-if="!gameOver" v-bind:style="{ color: currentPlayer === 'red' ? 'red' : 'yellow' }">It's {{ currentPlayer }}'s turn!</h4>
        <h4 v-if="gameOver">Game Over! {{ winner }} wins!</h4>
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
            rowPosition: ["1", "2", "3", "4", "5", "6"],
            columnPosition: ["a", "b", "c", "d", "e", "f", "g"],
            gameOver: false,
            winner: "",
            elementId: null,

        }
    },

    methods: {

        playChip(event) // function to play a chip
        {

            const cell = event.target; // get the element that was clicked
            this.elementId = cell.id.split("");

            //row = elementId[1]
            //column = elementId[0]


            if (!this.gameOver && !cell.classList.contains("red") && !cell.classList.contains("yellow") && cell.classList.contains("row")) // if the element does not have a color, cannot overwrite other play's chip
            {
                cell.classList.add(this.currentPlayer); // add the current player's color to the element
                this.checkWinCon(); // check for win conditions
                this.currentPlayer = this.currentPlayer === "red" ? "yellow" : "red"; // switch players
                
            }

            //need to create a function to check for win conditions
            //need to create a function to check for a tie
            //need to create a function to reset the board
            //need to fix an issue where column is changing color on click, this is also counting as a player's turn


        },
        //check for win conditions
        checkWinCon() {
            //check for horizontal win
            //searches only for win condition in the row (elementId[1]) that was last played --> saves computing power & memory
            for (let j = 0; j < this.columnPosition.length - 3; j++) {
                
                if (document.getElementById(this.columnPosition[j] +     this.elementId[1]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.columnPosition[j + 1] + this.elementId[1]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.columnPosition[j + 2] + this.elementId[1]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.columnPosition[j + 3] + this.elementId[1]).classList.contains(this.currentPlayer)) 
                {
                    
                    this.gameOver = true;
                    this.winner = this.currentPlayer;

                }
            }
    
            //check for vertical win
            //searches only for win condition in the column (elementId[0]) that was last played --> saves computing power & memory
            for (let i = 0; i < this.rowPosition.length - 3; i++) {

                if (document.getElementById(this.elementId[0] + this.rowPosition[i]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.elementId[0] + this.rowPosition[i + 1]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.elementId[0] + this.rowPosition[i + 2]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.elementId[0] + this.rowPosition[i + 3]).classList.contains(this.currentPlayer)) 
                    {
                    
                    this.gameOver = true;
                    this.winner = this.currentPlayer;
                
                    }
            }
                
            //check for diagonal win (negative slope) - rows increase, columns decrease
            for (let i = 0; i < this.rowPosition.length - 3; i++) {
                for(let j = 0; j < this.columnPosition.length - 3; j++) {
                    
                    if (
                    document.getElementById(this.columnPosition[j] + this.rowPosition[i]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.columnPosition[j + 1] + this.rowPosition[i + 1]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.columnPosition[j + 2] + this.rowPosition[i + 2]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.columnPosition[j + 3] + this.rowPosition[i + 3]).classList.contains(this.currentPlayer)
                    ) 
                    
                    {
                    
                    this.gameOver = true;
                    this.winner = this.currentPlayer;

                    }
                }
            }    

            //check for diagonal win (positive slope) - rows decrease, columns increase
            for (let i = this.rowPosition.length; i > 3; i--) {
                for(let j = 0; j < this.columnPosition.length - 3; j++) {
                    
                    if (
                    document.getElementById(this.columnPosition[j] + this.rowPosition[i]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.columnPosition[j + 1] + this.rowPosition[i - 1]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.columnPosition[j + 2] + this.rowPosition[i - 2]).classList.contains(this.currentPlayer) &&
                    document.getElementById(this.columnPosition[j + 3] + this.rowPosition[i - 3]).classList.contains(this.currentPlayer)
                    ) 
                    
                    {
                    
                    this.gameOver = true;
                    this.winner = this.currentPlayer;

                    }
                }
            }    




        } // end check win condition
    } // end methods
} // end export / default


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