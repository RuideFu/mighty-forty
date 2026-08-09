# **Installation Links**

## Fusion 360 / FreeCAD Setup:

[Fusion 360 Profile Setup and Download: ](https://www.autodesk.com/education/edu-software/fusion)

UNC Students have free access to the education version of Fusion 360. You will need to make an account using your school information. If your school does not offer free access to Fusion 360, you can sign up for a free trial through the website. If you do this, **BE SURE TO CANCEL THE TRIAL AT THE END OF THE WEEK.** Alternatively, you can download the FreeCAD software. FreeCAD is an opensource 3D Modeling software that works very well, it just lacks most of the quality of life features present with Fusion 360. On the upside, there is no project limit with FreeCAD. 

For non-UNC students (or those without access to Fusion 360):
[FreeCAD Installer Page: ](https://www.freecad.org/downloads.php)

### Fusion 360 Basic Tutorials

[This video](https://www.youtube.com/watch?v=7lKpzGtoQX0) by Design Forge is a little long, but goes over all of the essentials of 3D computer aided design (CAD) in fusion we will go over for this project.

Here is a list of some of the basic features and their functions: 
- Sketch – 2D profiles constrained with geometry/dimensions, the base for most 3D features.
- Extrude – Push/pull a sketch profile into a 3D solid or surface.
- Revolve – Rotate a profile around an axis to create round parts.
- Sweep – Move a profile along a path to create a solid.
- Loft – Blend between multiple profiles to form a transitional shape.
- Fillet/Chamfer – Round or bevel edges.
- Shell – Hollow out a solid, leaving a defined wall thickness.
- Pattern (Rectangular/Circular) – Duplicate features in a grid or radial array.
- Mirror – Copy features/bodies across a plane.
- Combine (Boolean) – Join, cut, or intersect bodies.
- Assemblies (Joints) – Connect components with motion-defining joints (rigid, revolute, slider, etc.).
- Parametric Timeline – History-based feature tree allowing edits/reordering.

### FreeCAD Basic Tutorials

[This video](https://www.youtube.com/watch?v=E14m5hf6Pvo) by Deltahedra is similarly long to the Fusion tutorial above, but also does a great job of showcasing all the basic features. 

Here is a list of the basic features of AutoCAD and what they do. I find it useful to have a short reference guide as the naming convention is slightly different from Fusion. 
- Sketcher – 2D constrained sketching workbench, foundation for Part Design features.
- Part Design (Pad) – Equivalent of extrude; turns a sketch into a solid.
- Revolution – Rotate a sketch profile around an axis.
- Sweep – Move a profile along a path to create a solid.
- Loft – Blend multiple sketches into one shape.
- Fillet/Chamfer – Round or bevel edges.
- Thickness (Shell) – Hollow out a solid to a set wall thickness.
- Pattern (Linear/Polar/Mirrored) – Duplicate features along a line, circle, or mirror plane.
- Boolean Operations (Part Workbench) – Union, cut, and intersection of solids.
- Assembly4 / Assembly Workbench – Position and constrain multiple parts into an assembly.
- Feature Tree (Parametric History) – Editable, reorderable list of applied features.

## Prusa Slicer Setup:

[Prusa Slicer Download: ](https://www.prusa3d.com/p/prusaslicer/)

Prusa Slicer is the software used to prepare models for printing with our 3D printer, a Prusa Mk4 Precision Printer. When you open the slicer for the first time you will be prompted to confirm some settings: 

- *Vendor*: 'Prusa FFF Printers'
- *Model*: 'Original Prusa MK4 Input Shaper' or 'MK4IS' 
- *Nozzle Diameter*: 0.4mm
- *Filament Type*: 'PLA' and 'PETG'
- Skip the Prusa SLA section

### Prusa Slicer Tutorials

Here is a [great intro video](https://www.youtube.com/watch?v=_kIqMPNQNSw&list=PLs1JXSLQ6-i6wekQWuthupCmNmsKa8nWg) from the youtube channel 3d Revolution going over all the basics of using Prusa Slicer. Aside from a few niche cases that likely won't come up, everything you need for this project should be in this video, however I am also attaching [the full playlist of prusa tutorials](https://www.youtube.com/playlist?list=PLs1JXSLQ6-i6wekQWuthupCmNmsKa8nWg) from this creator as they are very thorough. 

Some general tips for this project and 3D printing in general is to avoid using more than 25% infill in general, unless you are making a very small part that needs to be rock solid. There are a lot of different styles of infill, but I personally prefer 'monotonic' and 'gyroid' the most. You very rarely will need other styles of infill.

For supports, I always go with organic supports. they add more time to your prints than other forms of supports, but I find them to be far and away the easiest to remove. (They also look cool.)
