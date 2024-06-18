<template>
    <header>
        <h1>Checkers</h1>
    </header>
    <main>
        <div class="board">
            <div class="column" v-on:click="handleClick">
                <div class="row odd red" id="a1"></div>
                <div class="row even" id="a2"></div>
                <div class="row odd red" id="a3"></div>
                <div class="row even" id="a4"></div>
                <div class="row odd" id="a5"></div>
                <div class="row even" id="a6"></div>
                <div class="row odd white" id="a7"></div>
                <div class="row even" id="a8"></div>
            </div>
            <div class="column" v-on:click="handleClick">
                <div class="row even" id="b1"></div>
                <div class="row odd red" id="b2"></div>
                <div class="row even" id="b3"></div>
                <div class="row odd" id="b4"></div>
                <div class="row even" id="b5"></div>
                <div class="row odd white" id="b6"></div>
                <div class="row even" id="b7"></div>
                <div class="row odd white" id="b8"></div>
            </div>
            <div class="column" v-on:click="handleClick">
                <div class="row odd red" id="c1"></div>
                <div class="row even" id="c2"></div>
                <div class="row odd red" id="c3"></div>
                <div class="row even" id="c4"></div>
                <div class="row odd" id="c5"></div>
                <div class="row even" id="c6"></div>
                <div class="row odd white" id="c7"></div>
                <div class="row even" id="c8"></div>
            </div>
            <div class="column" v-on:click="handleClick">
                <div class="row even" id="d1"></div>
                <div class="row odd red" id="d2"></div>
                <div class="row even" id="d3"></div>
                <div class="row odd" id="d4"></div>
                <div class="row even" id="d5"></div>
                <div class="row odd white" id="d6"></div>
                <div class="row even" id="d7"></div>
                <div class="row odd white" id="d8"></div>
            </div>
            <div class="column" v-on:click="handleClick">
                <div class="row odd red" id="e1"></div>
                <div class="row even" id="e2"></div>
                <div class="row odd red" id="e3"></div>
                <div class="row even" id="e4"></div>
                <div class="row odd" id="e5"></div>
                <div class="row even" id="e6"></div>
                <div class="row odd white" id="e7"></div>
                <div class="row even" id="e8"></div>
            </div>
            <div class="column" v-on:click="handleClick">
                <div class="row even" id="f1"></div>
                <div class="row odd red" id="f2"></div>
                <div class="row even" id="f3"></div>
                <div class="row odd" id="f4"></div>
                <div class="row even" id="f5"></div>
                <div class="row odd white" id="f6"></div>
                <div class="row even" id="f7"></div>
                <div class="row odd white" id="f8"></div>
            </div>
            <div class="column" v-on:click="handleClick">
                <div class="row odd red" id="g1"></div>
                <div class="row even" id="g2"></div>
                <div class="row odd red" id="g3"></div>
                <div class="row even" id="g4"></div>
                <div class="row odd" id="g5"></div>
                <div class="row even" id="g6"></div>
                <div class="row odd white" id="g7"></div>
                <div class="row even" id="g8"></div>
            </div>
            <div class="column" v-on:click="handleClick">
                <div class="row even" id="h1"></div>
                <div class="row odd red" id="h2"></div>
                <div class="row even" id="h3"></div>
                <div class="row odd" id="h4"></div>
                <div class="row even" id="h5"></div>
                <div class="row odd white" id="h6"></div>
                <div class="row even" id="h7"></div>
                <div class="row odd white" id="h8"></div>
            </div>
        </div>
    </main>
</template>

<script>

export default {
    data() {
        return {
            currentPlayer: "red", // red goes first
            rowPosition: ["1", "2", "3", "4", "5", "6", "7", "8"],
            columnPosition: ["a", "b", "c", "d", "e", "f", "g", "h"],
            gameOver: false,
            winner: "",
            elementId: null,
            moveCounter: 0,
            possibleMovesCheck: false,
            possibleMoves: null,
            pieceMoving: null,

            // redPiece: { element: null },     // setting up for use of objects
            // whitePiece: { element: null }    // setting up for use of objects

        }
    },
    methods: {
        handleClick() {
            if(this.possibleMovesCheck === false) {
                this.checkPossibleMoves(event);
            } else {
                this.movePiece(event);
            }
        },
        checkPossibleMoves(event) {  // check if there are any possible moves
            
            let element = event.target;

            if(element.classList.contains("row")) {
    
                let row = element.id.charAt(1);
                let column = element.id.charAt(0);   
                
                this.possibleMoves = null;

                if(this.currentPlayer === "red") {

                    if(element.classList.contains("red")) {

                    this.possibleMoves = [
                    this.columnPosition[this.columnPosition.indexOf(column) - 1] + (parseInt(row) + 1),
                    this.columnPosition[this.columnPosition.indexOf(column) + 1] + (parseInt(row) + 1)
                ];
                    }

                } else if(this.currentPlayer === "white") {

                    if(element.classList.contains("white")) {

                    this.possibleMoves = [
                    this.columnPosition[this.columnPosition.indexOf(column) - 1] + (parseInt(row) - 1),
                    this.columnPosition[this.columnPosition.indexOf(column) + 1] + (parseInt(row) - 1)
                ];
                    }
                }

                if(this.possibleMoves) {

                    let possibleMove = document.getElementById(this.possibleMoves[0]);
                    if (possibleMove && !possibleMove.classList.contains("red") && !possibleMove.classList.contains("white")) {
                        possibleMove.classList.add("possibleMove");
                    
                    }
                    possibleMove = document.getElementById(this.possibleMoves[1]);
                    if (possibleMove && !possibleMove.classList.contains("red") && !possibleMove.classList.contains("white")) {
                        possibleMove.classList.add("possibleMove");
                    }
                    this.pieceMoving = element;
                    this.possibleMoves = document.getElementsByClassName("possibleMove");
                    
                this.possibleMovesCheck = true;
                
                }
        
            }
            // if not, game is over
            // if game is over, display winner
        },
        movePiece(event) {
            // if (this.gameOver) {
            //     return;
            // }

            let element = event.target;

            if(element === this.pieceMoving) {
                for (let i = this.possibleMoves.length - 1; i >= 0; i--) {
                        this.possibleMoves[i].classList.remove("possibleMove");
                    }
                this.possibleMovesCheck = false;
                return;
            }

            if(element.classList.contains("row") && element.classList.contains("odd") && element.classList.contains("possibleMove")) {
                   
                    element.classList.add(this.currentPlayer);
                    this.pieceMoving.classList.remove(this.currentPlayer);
                    this.moveCounter++;
                    this.currentPlayer = this.currentPlayer === "red" ? "white" : "red"; // switch players
                    

                    for (let i = this.possibleMoves.length - 1; i >= 0; i--) {
                        this.possibleMoves[i].classList.remove("possibleMove");
                    }
                    this.possibleMovesCheck = false;
            }
        }
    }
}

</script>

<style scoped>
/* Style for each of the columns on the board */

.board {
    display: flex;

    flex-direction: row;

    height: fit-content;
    width: fit-content;

    border: 1px solid black;
    background-color: black;


}

.column {
    display: flex;

    flex-direction: column;

    height: 100%;
    width: 100%;

    justify-content: space-evenly;

}

/* Style for each of the rows on the board, with access to each piece in that row */
.row {
    display: flex;
    flex-direction: row;
    height: 100px;
    width: 100px;

    justify-content: space-evenly;
}

.odd {
    background-color: black;
}

.even {
    background-color: red;
}

.red {

    background-color: red;
    border-radius: 50%;
    scale: 85%;
}

.white {

    background-color: white;
    border-radius: 50%;
    scale: 85%;
}

.possibleMove {
    background-color: green;
    border-radius: 50%;
    scale: 25%;
    opacity: 0.5;
}
</style>