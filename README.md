
- [Learning and Development](#learning-and-development)
  - [Prerequisites](#prerequisites)
  - [What is SVG?](#what-is-svg)
    - [Container Element](#container-element)
    - [viewport](#viewport)
    - [viewBox](#viewbox)
    - [Relationship between coordinate system and viewBox](#relationship-between-coordinate-system-and-viewbox)
    - [Basic Shapes](#basic-shapes)
      - [Application of the Basic Shapes](#application-of-the-basic-shapes)
    - [Elements](#elements)
      - [Basic Shapes Elements](#basic-shapes-elements)
      - [Path Element](#path-element)
    - [Styling and geometry properties](#styling-and-geometry-properties)
      - [Ways to style an SVG](#ways-to-style-an-svg)
    - [SVG Animation](#svg-animation)
  - [Where to get SVG files?](#where-to-get-svg-files)

# Learning and Development
By: Allan Adan

## Prerequisites
1. HTML
2. CSS
3. JavaScript
## What is SVG? 
 - scalable vector graphics
 - A language for describing 2D graphics
- Fir simpler definition, it is an XML for web graphics
- One of the benefits of using the SVG file is that they are resolution independent, which means they can scale infinitely.
### Container Element

- When we add an svg element, the user-agent of the browser creates a viewport coordinate system and that will allow us to create graphical content.

- To create a **viewport**, we have to add the height and width attributes. Values can be numbers or pecentages. Default values are 300px x 150px.

      <svg width="100%" height="100%">
          <!-- Graphical contents here -->
      </svg>

### viewport

- Default size is 300px x 150px.

      <svg width="300" height="150">
          <!-- Graphical contents here -->
      </svg>

### viewBox

- is an SVG attr to set image box
- Syntax: ``viewBox="z y width height"``
  
      <svg width="100%" height="100%"
          viewBox="0 0 15360 15120">
          <!-- Graphical contents here -->
      </svg>

### Relationship between coordinate system and viewBox 


  | viewport coordinate system | local coordination system |
  | -------------------------- | ------------------------- |
  | x                          | min_x                     |
  | y                          | min_y                     |
  | width                      | viewBox_width             |
  | height                     | viewBox_height            |
  |                            |                           |

    <svg x="x" y="y" width="width" height="height"
          viewBox="min_x min_y viewBox_width viewBox_height">
          <!-- Graphical contents here -->
      </svg>

  |                   | viewport                   | viewBox                 |
  | ----------------- | -------------------------- | ----------------------- |
  | coordinate system | viewport coordinate system | local coordinate system |
  | position          | x, y                       | min_x, min_y            |
  | size              | width, height              | viewBox_width, viewBox_height |

### Basic Shapes

1. Rectangle
2. Circle
3. Ellipse
4. Line
5. Polyline
6. Polygon

All of the above shapes are the equivalent to the path element.

#### Application of the Basic Shapes

By using the paint properties such as fill, basic shapes can be used to draw such as fill, stroke, and markers. Moreover, basic shapes can be used as a clipping mask.
### Elements
#### Basic Shapes Elements
1. \<rect>
   - defines a rectangle that is aligned along the x and y axis.
   - Geometric properties: 
     - x 
       - an indent from the beginning of the local coordinate system along the x-axis to the left edge of the rectangle.
     - y
       - an indent from the beginning of the local coordinate system along the y-axis to the left edge of the rectangle.
     - width
       - width of the rectangle from the x point
     - height
       - width of the rectangle from the y point
     - rx
       - the corner's radius along the x-axis
     - ry 
       - the corner's radius along the x-axis
   - The rx and ry geometry property are used to define the radii of the elliptical arcs that is used to round the corners of the rectangle.

2. \<circle>
    - defines a circle element
    - Geometric properties: 
      - cx
        - an offset from the beginning of the local coordinate system on x-axis to the central point of the circle.
      - cy
        - an offset from the beginning of the local coordinate system on y-axis to the central point of the circle.
      - r
        - radius of the circle
  
3. \<ellipse>
    - defines an ellipse aligned in the current local coordinate system on the x,y axis. Unlike the circle, the ellipse element has two radii - one for the x and one for the y-axis.
    - Geometric properties:
      - cx
        - an offset from the beginning of the local coordinate system on x-axis to the central point of the ellipse.
      - cy
        - an offset from the beginning of the local coordinate system on x-axis to the central point of the ellipse.
      - rx
        - radius of the ellipse along the x-axis
      - ry
        - radius of the ellipse along the x-axis

4. \<line>
   - defines the line segment that starts at one point and ends at another.
   - Geometric properties:
     - x1
       - speficifies the indentation of the start point of the line from the beginning of the local coordinate system along the x-axis.
     - y1
       - speficifies the indentation of the start point of the line from the beginning of the local coordinate system along the y-axis.
     - x2
       - speficifies the indentation of the end point of the line from the beginning of the local coordinate system along the x-axis.
     - y2
       - speficifies the indentation of the end point of the line from the beginning of the local coordinate system along the y-axis.

5. \<polyline>
    - defines an open shape. A set of connected straight lines. That means that the start and end points of the polyline are never connected and do not create a closed contour. Even if the coordinates of the start and end point are the same.
    - points
        - **not a geometric property. You cannot change it through CSS**
        - determines the coordinates of the polyline points. The point value is a list of value separated by spaces, commas, or spaces and commas.
            ``points = <<x1,y1,x2,y2...>>``
        - If the number of coordinate is odd, the last coordinate is discarded and the shape is built without it.

6. \<polygon>
   - defines a closed shape. It consists of a set of connected straight lines. Unlike polyline, the polygon element's last and first points are connected by a straight line.
   - points
     - **not a geometric property. You cannot change it through CSS**
     - determines the coordinates of the polygon points. The point value is a list of value separated by spaces, commas, or spaces and commas.
           ``points = <<x1,y1,x2,y2...>>``

#### Path Element
1. \<path>
   - defines the outline of the shape.
   - Uses:
     - Shape Creation
       - can be filled or stroked. 
     - Clipping path
       - can be used as a clipping path
     - Creating an animation
     - Create text on a path
   - The path element is described by using the concept of the current point. 
   - Cuurent Point
     - cpx (current point x)
     - cpy (current point y)
     - When you draw a straight line or curve, it starts from the current point and move along the line of the curve that follows after it. 
   - The path represents the outline defined by the following:
     - moveTo(M,m)
       - set the current point
     - lineTo(L,l)
       - draw the straight line
     - curveTo(C,c,S,s)
       - draw a cubic or quadratic bezier
     - arc(Q, q, T, t)
       - draws an elliptical arc
     - closePath(Z,z)
       - closes the current outline by connecting the current point with the start point.
   - d 
     - The d property, or, in other words, path data may contain all of the above statements. It has a concise syntax for minimizing the file size and for more efficient download.
   - Syntax
     - M moveTo
       - M 100 100
       - d = "M x y x1 y1 x2 y1 x2 y m x3 y3 x4 y4"
     - L lineTo
       - L 200 100
       - L 200 100 -100 -200
       - d = "M x y L x1 y1 H x2 V y2"
     - C curveTo
       - d = "M x0 y0 C x1 y1 x2 y2 x y"
       - d = "M x0 y0 C x1 y1 x2 y2 x y S x4 y4 x3 y3"
     - A arc
       - d = "M x0 y0 Q x1 y1 x y T x2 y2"
     - Z closePath
       - d = "M x y L x1 y1 x2 y2 Z"
       - d = "M x y L x1 y1 x2 y2 z"
     - M, L, C, S, Z (Uppercase)
       - uppercase means absolute coordinates
     - m, l, c, s, z (Lowercase)
       - lowercase means relative coordinates


### Styling and geometry properties

#### Ways to style an SVG

1. Inline stylesheet: \<style> element

  - add style element inside \<svg> element.
  
2. external stylesheet: \<link> element
   
  - using the link element, specify the href, type="text/css", rel="stylesheet" attribute. 
  
3. style attribute
   
  - add style attribute to the element we want to style. value should be css rules that are separated by semicolon.
  
4. presentation atributes
  
  - attributes that have similar names with a particular CSS properties and whose values are parsed as the values of the particular properties.
  - Example:
    - SVG fragment where styles have the presentation attributes
      - ``<rect x="20" y="20" width="100" height ="50" fill="green" stroke="blue" />``
    - CSS style
      - ``rect { fill: green; stroke: blue }``

### SVG Animation

1. SVG's animation elements
   - animate
   - animateMotion
   - animateTransform
   - discard
   - set



## Where to get SVG files?
1. https://www.svgrepo.com/collections/
2. https://vectormaker.co/
3. https://svgapi.com/