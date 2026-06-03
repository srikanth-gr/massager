<!-- METADATA_START -->
- **File Name**: tennis-ball-holder.md
- **Version**: fac7895
- **Last Commit Date**: 2026-06-03
- **Last Comment**: V4 design - saddle rail system, snap clip enclosure.
<!-- METADATA_END -->

# Project Requirements: Shoulder Massage Tennis Ball Holder

## 1. Functional Objective
Design a heavy-duty mechanical shoulder massage tool that holds a standard tennis ball. The ball must roll smoothly under full body weight load to relieve deep muscle tension. The design uses a passive concave saddle rail system for constrained single-axis rolling with no axle or hardware passing through or contacting the ball.

## 2. Mechanical Design & Motion Profile
- Axis of Rotation: Single-axis (X-axis). The ball spins in place like a wheel/roller to follow shoulder stroke direction.
- Retention System: Concave saddle rail. Each yoke arm has a curved inner channel (6mm deep, radius matching ball curvature) that cradles the ball along a line of contact. No axle, no pins, no hardware near the ball cavity.
- Top Enclosure: Snap clip latch across the top of the yoke. Prevents vertical ejection of the ball under downward or lateral body weight load.

## 3. Structural Integrity & Rigidity
- Load Support: Must survive full human body weight pressed against a wall or floor without fracture, slip, or delamination.
- Component Dimensions (V4 Layout):
  - Base Footprint: 110mm x 80mm stabilizing foundation block.
  - Base Thickness: 15mm minimum solid thickness.
  - Support Towers (Yoke): 22mm thick reinforced vertical side walls.
  - Saddle Rail Depth: 6mm concave channel on each arm inner face.
  - Ball Cavity: Spherical cutout at 33.5mm radius (67mm diameter tennis ball).
- No through-bore. The ball cavity is fully open on the axle axis; retention is handled entirely by the saddle rails and snap clip.

## 4. Software & CAD Strategy
- Environment: FreeCAD (Python Macro Automation).
- API Compatibility: Scripted using Part workbench primitives (Part::Box, Part::Cylinder, Part::Sphere) and boolean operations (Part::Fuse, Part::Cut). No PartDesign workbench dependencies.
- Saddle Rail Geometry: Modelled as a Part::Sphere boolean cut along each arm inner face, radius 33.5mm, depth 6mm, centered on ball equator.
- Snap Clip: Modelled as a thin Part::Box bridge across the yoke top with a small interference-fit notch for retention.

## 5. FreeCAD Python Macro
Will be maintained in a separate file outside this md.


## 6. Design History & Evolution
1. V1 (Static Cup): Single-piece solid cylinder holding the ball passively. Superseded to enable rolling.
2. V2 (Vertical Pin Pivot): Two-part assembly with base pin and free-spinning dual-claw arm for 360-degree rotation. Superseded due to load limitations and ball slip risk.
3. V3 (Industrial Over-Center Yoke MVP): Thick 22mm arms with continuous metal through-bolt on X-axis. Superseded because the through-axle blocks a real tennis ball from being mounted.
4. V4 (Saddle Rail Yoke): Current design. No axle or hardware contacts the ball. Retention via 6mm deep concave saddle rails on each arm inner face plus a snap clip latch across the yoke top. Smooth controlled X-axis roll under full body weight.