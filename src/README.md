Hello,

The above JS code contains the following sections:

1.Draw Shapes

2.Collision

Intro----------------------------------------------------------------------------------------------------------
    
    1.Draw a stage and add two layers [layer and layer1]
    2.layer for drawing
    3.layer1 for drawing and collision

Draw Shapes-----------------------------------------------------------------------------------------------------
    
    This section contains the following steps:
    1.First, Create a context variable
    2.On the mouse event listeners using 'stage.on' functions
    3.If mouse Down
        -Put (draggable=true) as we are going to drag the pointer.
        -Get initial Pointer positions and place it in LastPos variable.
    4.If mouse move
         -check for draggable
         -if mode is 1 (initial)
               #Take (Final-intial) values.
               #Draw square on canvas.
         -if mode is 2
               #Take (Final-intial) values.
               #Draw Circle on Canvas.
     5.If mouse up
          -if mode is 1
               #Draw Square in layer using Konva and clear the canvas.
               #set mode=2
          -if mode is 2
               #Draw Circle in Layer1 [As we need to use it for collision]
               #make it draggable [for collision]
               #remove event Listeners
               #transfer control to mini squares
      6.Minisquares
           -Create a Group
           -For each group draw a square of unit size of Original Square [0.06% for square and remaining 0.04% for border]
           -Add group to layer1      [As we need to use it for collision]
           
 Collision----------------------------------------------------------------------------------------------------------------
      
     1.Event 
            -Create event listener for Dragmove using konva
            -Now take the target [draggable object] and find its ClientRect using getClientRect() [store in targetRect]
            -send the targetRect and group [minisquares] to collision check function.
            -if returns true [make it invisible]
            -else if returns false [make it visible]
     2.Check function
            -With the targetRect as input find the circle radius using targetRect initial coordinates.
            -circle center = targetRect coordinate X - {width} [slly for Y]
            -Then check for various conditions of collision
            
 [NOTE: IN THIS PROGRAM, AFTER CHECKING COLLISION THE COLOR OF THE MINIRECTS WAS CHANGED, BUT WE CAN EVEN 
  MAKE THEM INVISIBLE BY USING 'VISIBLE' PROPERTY]          
