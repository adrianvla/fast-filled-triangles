This is a fixed point algorithm made to render filled triangles. (scanline, bresenham)

How it works:
  1. It sorts the points so that y0<=y1<=y2
  2. It then calculates the line [y0,y2] and stores it in hyp (a buffer), which stores the distance of a point of the line to x0 if x2>=x0.      If x2<x0, it flips the line and stores the distance to x0.
  3. Now, it renders [y0,y1] using bresenham and fills (scanline) the distance from a point of the line to [y0,y2] using the buffer
  4. Then it renders [y1, y2] and does the same



Normally the program stores (y2-y0) times uint in hyp, but I didn't make it dynamically allocated to improve speed.

W and H are the width and height of the display buffer (or wherever you want to fill the triangle), and f is the pointer to the function used by the program to place a pixel.

renderer.c has:
  1. ```cpp
     drawTriangle (int x0, int y0, int x1, int y1, int x2, int y2, uint8_t r, uint8_t g, uint8_t b, uint8_t a, uint W, uint H, uint8_t* pixels, void (*f)(uint,uint,uint8_t,uint8_t,uint8_t,uint8_t,uint,uint,uint8_t*))
     ```
  2. ```cpp
     drawline (int x1, int y1, int x2, int y2, uint8_t r, uint8_t g, uint8_t b, uint8_t a, uint W, uint H, uint8_t* pixels, void (*f)(uint,uint,uint8_t,uint8_t,uint8_t,uint8_t,uint,uint,uint8_t*))
     ```

The function f needs the following arguments:
  1. uint X
  2. uint Y
  3. uint8_t r
  4. uint8_t g
  5. uint8_t b
  6. uint8_t a
  7. uint8_t r
  8. uint W
  9. uint H
  10. uint8_t* pixels (the buffer where you want to render)

TODO:
  clean up code
  add ifs instead of inline ones to improve speed even further
  

If you use this in your projects, it'd be nice if you credited me, but optionnal. :)
