---
layout: default
permalink: /projects/ortho_project/
weight: 1
---

Abstract
--------
Many 3D CAD models are represented by 2D drawings from several
different orthographic views. Utilizing algorithms that exploit the
orthographic nature of the 2D drawings, a 3D wireframe can be created
using DXF files that correspond to the “Front”, “Top”, and “Side”
orthographic representations of a 3D object.

Motivation
----------
Hardware vendors often only distribute 2D engineering drawings to
customers, resulting in a designer recreating the part in order to
incorporate it into their CAD design. This project is an attempt to begin
to automate this inefficiency through computational geometry. The end
goal would be a system that can take many different formats of 2D
drawings and recreate an accurate 3D object using only those drawings
and minimal input from a human user.

![Orthographic Basics](/assets/ortho_project/im1.png)

Figure 1: A simplified representation of a basic 3-view orthographic projection.

![Orthographic Basics](/assets/ortho_project/im2.png)

Figure 2: A more complex orthographic representation with multiple detailed and cross-section views.


Theory
------

Each orthographic drawing can be treated as a connected graph, where
graph nodes are vertices in the drawing, or intersection points between
2 or more non-parallel lines. A connected graph is made for each
orthographic view, and these connected graphs can then be processed
into a 3D wireframe of the object.

Method
------

1. 3D models were created using a CAD program to test the algorithm.

2. Individual DXF files of each orthographic view (“Front”, “Top”, “Side”) of
a model are created and then processed into (X,Y), (X,Z), and (Y,Z)
coordinates representing start and end nodes that are connected by
edges. All possible edges between nodes given the actual drawing are
created. Not all generated edges are necessarily representative of an
actual edge in the 3D model, but this process ensures that no edges that
might be viable are missed due to the edge representation in the DXF
file input. Through this process a list of nodes and an adjacency matrix
representing edges between nodes is created for each orthographic
view.

3. Next the algorithm uses the nodes and adjacency matrix for each
orthographic view to compare and match potential 3D edges. By
comparing all adjacency matrices it is possible to surmise a 3D edge if in
every orthographic view there is either an edge connection or a point
correspondence. At the end of this process a 3D “skeleton” of edges has
been created that represents the object’s shape.

![Edge calculation](/assets/ortho_project/im3.png)

Figure 3: Simplified representation showing all possible and acceptable edges between 3 nodes.


Results
-------

Several different shape recreations were attempted. Simple objects such
as those shown below were accurately recreated. Shown below are 2 successful examples of the edge calculation process. The images follow the process described in the Method section, whereby a 3D model is generated, an orthographic DXF image of that 3D model is generated, and a wireframe diagram of the DXF is then calculated.

![First part](/assets/ortho_project/im4.png)
![First part](/assets/ortho_project/im5.png)
![First part](/assets/ortho_project/im6.png)

![Second part](/assets/ortho_project/im7.png)
![Second part](/assets/ortho_project/im8.png)
![Second part](/assets/ortho_project/im9.png)

Larger, more complex models and models with curves or edge cuts could
not be accurately recreated by the algorithms, as seen in the images below:

![Third part](/assets/ortho_project/im10.png)
![Third part](/assets/ortho_project/im11.png)
![Third part](/assets/ortho_project/im12.png)

![Fourth part](/assets/ortho_project/im13.png)
![Fourth part](/assets/ortho_project/im14.png)
![Fourth part](/assets/ortho_project/im15.png)

Future Work
-----------

Several different avenues for improvement are possible:

1. Accurate 3D reconstruction of more complex geometry such as that
used in real engineering drawings.
2. Complete 3D reconstruction rather than only wireframe
construction.
3. Improved performance for parts with many edges.
4. Reconstruction for specific views such as cross-section or detailed
views.
5. Conversion of different file types besides DXF, such as PDF, JPEG, or
PNG into useable coordinates for vertex and edge reconstruction.

References
----------

1. Wesley, Michael. Markowsky, George. 1981. “Fleshing Out
Projections: Reconstruction of Objects”
2. Furferi, Rocco, et. al. 2010. “From 2D Orthographic Views to 3D
Pseudo-Wireframe: An Automatic Procedure”
3. Carfagni, Monica, et. al. 2011. “3D Reconstruction Problem: An
Automated Procedure”


Links
-----

Below is the link to the Github repository (not cleaned up, sorry!):

[Github](https://github.com/amarschn/cv_orthographic_reconstruction)
![Poster](/assets/ortho_project/poster.png)

