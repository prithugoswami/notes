---
geometry:
- lmargin=0.9in
- rmargin=0.3in
- tmargin=0.3in
- bmargin=0.5in
- twoside
papersize: A4
...

## Point function

```
glBegin (GL_POINTS)
    glVertex* ();
glEnd();
```

- `glVertex()` function is used to specify coordinates of any point on OpenGL
- `*` represents the suffix required
  - a number 2,3 or 4 specify the dimensionality
  - two dimensional coordinates *(x,y)* is actually a 3d coordinate where z =
    0. So *(x,y)* = *(x,y,0)*. Moreover OpenGl represents vertices as four
    dimensions.
  - suffix code for indicating the data type is as follows: i (integer), s
    (short), f (float) and d (double)
  - If we use an array to indicate the coordinates of the vertex then we append
    a `v`

- **Examples:**

```
        glBegin(GL_POINTS)
            glVertex2i(50, 100);
            lVertex2i(75, 150);
            glVertex2i(100, 200);
        glEnd();

        int point1[] = {50, 100};
        int point2[] = {75, 150};
        int point3[] = {100, 200};

        glBegin(GL_POINTS)
            glVertex2iv(point1);
            glVertex2iv(point2);
            glVertex2iv(point3);
        glEnd();
```

## Line Functions

Three line primitive constants:

1. `GL_LINES`
2. `GL_LINE_STRIP`
3. `GL_LINE_LOOP`


