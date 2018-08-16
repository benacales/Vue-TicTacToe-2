<template>
<div>
  <div class = "playSpace" >
        <BoardSpace v-for="(row, i) in board" :key="i" :value = "row" :position="i" @makeMove = "makemove"></BoardSpace>
    </div>
</div>

</template>
<script>
import Hello from './components/Hello.vue'
import BoardSpace from './components/boardSpace.vue'

export default {
  name: 'app',
  components: {
    Hello,
    BoardSpace
  },
  data() {
    return {
      board: [
          0,
          0,
          0,
          0,
          0,
          0,
          0,
          0,
          0
      ],
      currentPlayer: 1
    }
  },
  methods: {
      makemove(position){
          console.log ("position " , position);
          var newBoard = Array.from(this.board)
          if (newBoard[position] !== 0) {
              return;
          }
          newBoard[position] = this.currentPlayer;
          this.board = newBoard;
          if (this.currentPlayer === 1) {
              this.currentPlayer = 2;
          }
          else {
              this.currentPlayer = 1;
          }
          setTimeout(() => {
              this.checkwin(); 
          }, 200);
      },
      checkwin() {
          var box1 = this.board[0]
          var box2 = this.board[1]
          var box3 = this.board[2]
          var box4 = this.board[3]
          var box5 = this.board[4]
          var box6 = this.board[5]
          var box7 = this.board[6]
          var box8 = this.board[7]
          var box9 = this.board[8]

          var winner = null;

              // The X Team
          if ((box1 === 1) && (box2 === 1) && (box3 === 1)) {
              winner = 1;
          }
          if ((box4 === 1) && (box5 === 1) && (box6 === 1)) {
              winner = 1;
              }
          if ((box7 === 1) && (box8 === 1) && (box9 === 1)) {
              winner = 1;
              }
          if ((box1 === 1) && (box4 === 1) && (box7 === 1)) {
              winner = 1;
              }
          if ((box2 === 1) && (box5 === 1) && (box8 === 1)) {
              winner = 1;
              }
          if ((box3 === 1) && (box6 === 1) && (box9 === 1)) {
              winner = 1;
              }
          if ((box1 === 1) && (box5 === 1) && (box9 === 1)) {
              winner = 1;
              }
          if ((box3 === 1) && (box5 === 1) && (box7 === 1)) {
              winner = 1;
              }
          // The O Team
          if ((box1 === 2) && (box2 === 2) && (box3 === 2)) {
              winner = 2;
              }
          if ((box4 === 2) && (box5 === 2) && (box6 === 2)) {
              winner = 2;
              }
          if ((box7 === 2) && (box8 === 2) && (box9 === 2)) {
              winner = 2;
              }
          if ((box1 === 2) && (box4 === 2) && (box7 === 2)) {
              winner = 2;
              }
          if ((box2 === 2) && (box5 === 2) && (box8 === 2)) {
              winner = 2;
              }
          if ((box3 === 2) && (box6 === 2) && (box9 === 2)) {
              winner = 2;
              }
          if ((box1 === 2) && (box5 === 2) && (box9 === 2)) {
              winner = 2;
              }
          if ((box3 === 2) && (box5 === 2) && (box7 === 2)) {
              winner = 2;
              }

          if (winner == null) {
              return
          } else {
              alert("Player " + winner + " wins!")
              this.resetBoard()
          }
      },
      resetBoard() {
          this.currentPlayer = 1;
          this.board = [
          0,
          0,
          0,
          0,
          0,
          0,
          0,
          0,
          0
          ]
      }
  }
}
</script>

<style>
html {
    background-color : #717A8B;
    height : 100%;
    width : 100%;
}
header {
    background-color : blanchedalmond;
    height : 100%;
    width : 98.5%;
    border : solid;
    border-color : black;
    border-width : 3px;
    padding-top : -2em;
    padding-bottom : 1em;
    padding-left : 1.5em;
    margin-bottom : 1em;
}



.playSpace {
    display : grid;
    grid-template-columns : 12vw 12vw 12vw;
    grid-template-rows : 12vw 12vw 12vw;
}

.box {
    margin : 1vw;
    height: 10vw ;
    width : 10vw;
    border : solid;
    border-width: .25vw;
    border-color: rgb(153, 255, 0);
    justify-content: center;
    align-items : center;
    vertical-align: middle;
}
.theBox {
    height: 10vw;
    width : 10vw;
    justify-content: center;
    align-items : center;
    vertical-align: middle;
}
.fa-circle-thin {
    font-size: 900%;

}
.fa-times {
    font-size: 900%;

}
div.tooltip {	
    position: absolute;			
    text-align: center;			
    width: 60px;					
    height: 28px;					
    padding: 2px;				
    font: 12px sans-serif;		
    background: lightsteelblue;	
    border: 0px;		
    border-radius: 8px;			
    pointer-events: none;			
}
</style>