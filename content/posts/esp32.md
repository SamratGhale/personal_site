+++
title = 'Chess inside Esp32'
date = 2024-07-06
draft = false
+++

This is my blog documenting the process of creating a chess engine and running it in a esp32.


The project has 4 seperate parts

1. The chess engine
2. Chess AI
3. ESP32 ui
4. ESP32 Networking

I will be dealing with these topic in the given order. And I'll be updating the code in this [repo](https://github.com/SamratGhale/chessmate).

## Move calculation
The chess engine needs to calculate the possible move a piece can make
It should check where the piece is which positions can the piece moves into

I have Implemented a very basic version of the move calculation (only for pawn and knight fow now) shown below.


<!--more-->
<div id='viz1504830938123'>
<video width="700" height="400" controls>
  <source src="/chess_first_demo.mp4" type="video/mp4">
</video>
</div>

# Implementation

Everytime the player clicks on the piece the engine calculates the possible moves in the linked list.

```c
typedef struct Move Move;
struct Move
{
  Pos start, end;

  Move* next;
};

typedef struct{
  CMPieces  pieces[64];
  Pos       selected;
  Move*     possible_moves;
  Texture2D textures[13]; //leave the first one blank because it's none
  char* fen;
}CMBoardState;

```

And when the player clicks on one of the position in the list. It moves the piece to that position

```c
bool cm_make_move(CMBoardState* board, Pos p){

  Move* curr = board->possible_moves;

  bool found = false;

  while(curr){
    if(is_pos_equal(curr->end, p)){
      found = true;

      CMPieces piece = cm_get_piece_from_pos(board, curr->start);
      i8 i = cm_pos_to_index(curr->start.x , curr->start.y);
      board->pieces[i] = NONE;
      board->pieces[cm_pos_to_index(curr->end.x, curr->end.y)] = piece;

      //
    }
    curr = curr->next;
  }

  return found;
}

```