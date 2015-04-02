# Final Project Assignment 2: Explore One More! (FP2) 
DUE March 30, 2015 Monday (2015-03-30)

Name: Jerra Khorn

My Library: [arrow.rkt](http://docs.racket-lang.org/teachpack/arrow.html?q=)

I wanted to use look into this library because I changed that idea of what my project.
I was interesting in maybe a pacman/maze like game and so I was interested in
moving images. the arrow.rkt library looked promising and through it I would
be able to move images with a controller GUI.

```
#lang racket
(require htdp/draw)
(require htdp/arrow)
(require lang/posn)

;Shape is a structure
;    (make-posn number number)

;define radius
(define RAD 10)

;make canvas
(start 300 300)

(define (draw-it shape)
  (draw-solid-disk shape RAD))

(define (translate-x shape change)
  (make-posn (+ (posn-x shape) change) (posn-y shape)))

(define (translate-y shape change)
  (make-posn (posn-x shape) (+ (posn-y shape) change)))

(define (move-x delta shape)
  (cond
    [(and (clear-solid-disk shape RAD)
          (draw-solid-disk (translate-x shape delta) RAD))
     (translate-x shape delta)]
    [else false]))
 
(define (move-y delta shape)
  (cond
    [(and (clear-solid-disk shape RAD)
          (draw-solid-disk (translate-y shape delta) RAD))
     (translate-y shape delta)]
    [else false]))

(control (make-posn 10 10) 10 move-x move-y draw-it)
```

This is my code. It makes a canvas and a controller GUI. Through the controller, a disk is created and
by clicking on the arrows the object can move in that direction.

[Initial Start](http://i.imgur.com/R6Nftlh.png)
[After many clicks on the controller GUI to get the disk in the middle of the canvas](http://i.imgur.com/Zo2IxwP.png)
