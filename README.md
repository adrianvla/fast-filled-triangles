This is a fixed point algorithm made to render filled triangles. (scanline, bresenham)

How it works:
  1. It sorts the points so that y0<=y1<=y2
  2. Then it calculates the line [y0,y2] and stores it in hyp (a buffer), which stores the distance of a point of the line to x0 if x2>=x0 and x2 if x2<x0
  3. It renders [y0,y1] using bresenham and fills (scanline) the distance from a point to [y0,y2] using the buffer
  4. Then it renders [y1, y2] and does the same



Normally the program stores (y2-y0) times int in hyp, but I didn't make it dynamically allocated to improve speed
