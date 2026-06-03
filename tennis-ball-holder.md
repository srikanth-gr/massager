<!-- METADATA_START -->
- **File Name**: tennis-ball-holder.md
- **Version**: 5f4a3d0
- **Last Commit Date**: 2026-06-03 12:15:20 +0200
- **Last Comment**: Axle connected to ball grip.
<!-- METADATA_END -->

# Project Requirements: Shoulder Massage Tennis Ball Holder

## 1. Functional Objective
Design a heavy-duty mechanical shoulder massage tool that holds a standard tennis ball. The ball rolls smoothly under full body weight load via two rotating concave cups mounted on the yoke arms. Each cup spins freely on its integrated axle stub, allowing controlled single-axis rolling along the X-axis.

## 2. Mechanical Design & Motion Profile
- Axis of Rotation: Single-axis (X-axis). Ball rolls like a wheel to follow shoulder stroke direction.
- Retention System: Two concave rotating cups, one per arm, each cradling the ball at the equator. The cups rotate with the ball on the X-axis.
- Cup Mounting: Each cup has an integrated cylindrical axle stub (8mm dia, 38mm long) centered at the cup midpoint, which aligns with the ball equator. The stub inserts into a single circular bore on the arm inner face and locks via a retention lip.

## 3. Structural Integrity & Rigidity
- Load Support: Must survive full human body weight pressed against a wall or floor.
- Component Dimensions (V5 Layout):
  - Base Footprint: 120mm x 80mm.
  - Base Thickness: 15mm minimum.
  - Support Arms (Yoke): 22mm thick each.
  - Arm Cavity (between arms): 76mm.
  - Cup Dimensions: 28mm thick x 72mm diameter each (56mm total).
  - Concave Face Radius: 33.5mm matching ball surface.
  - Axle Stub: 8mm diameter cylinder, 38mm long, centered at cup midpoint. Built into the flat side of the cup.
  - Retention Lip: 5mm radius ring at axle tip.
  - Axle Clearance per side: 10mm.
  - Ball Cavity: 33.5mm radius spherical cutout.

## 4. Parts List
1. Yoke body x1 — PLA or PETG. Single print, base flat on bed.
2. Rotating cup x2 — PETG. Axle stub integrated. Print concave face up.
No hardware required. Fully self-contained printed assembly.

## 5. Software & CAD Strategy
- Environment: FreeCAD (Python Macro Automation).
- API: Part workbench primitives and boolean operations only. No PartDesign dependencies.
- Cup geometry: Box body with sphere boolean cut on front face for concave profile. Cylinder fused on back face at midpoint for axle stub. Retention lip cylinder fused at stub tip.
- Right cup: mirrored from left cup along X-axis centerplane.

## 6. Design History & Evolution
1. V1 (Static Cup): Single-piece cylinder holding ball passively. Superseded to enable rolling.
2. V2 (Vertical Pin Pivot): Two-part assembly with free-spinning dual-claw arm. Superseded due to load limitations.
3. V3 (Over-Center Yoke): Thick 22mm arms with metal through-bolt. Superseded as through-axle blocks real ball.
4. V4 (Saddle Rail Yoke): Concave saddle rails with snap clip. Superseded as clip blocked massage access.
5. V5 (Rotating Cup Yoke): Current design. Two concave rotating cups with integrated cylindrical axle stubs centered at ball equator. Ball rolls freely on X-axis. No hardware required.