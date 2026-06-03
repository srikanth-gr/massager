<!-- METADATA_START -->
- **File Name**: tennis-ball-holder.md
- **Version**: 6a44f45
- **Last Commit Date**: 2026-06-03 12:22:07 +0200
- **Last Comment**: V6 design - Round base, blind axle pockets, open-jaw narrow arms.

# Project Requirements: Shoulder Massage Tennis Ball Holder

## 1. Functional Objective
Design an industrial-grade, heavy-duty shoulder massage tool that holds a standard tennis ball. The device must withstand full human body weight when pressed against a wall or floor. The assembly features a dual-axis load architecture: lateral retention and tracking via rotating side cups with integrated fingerprint-grip textures, and vertical load-bearing via a free-spinning center wheel embedded into the base foundation floor.

## 2. Mechanical Design & Assembly Profile
- **Axis of Rotation:** Single-axis (X-axis) rolling alignment.
- **Base Geometry:** Circular cylindrical foundation ($120\text{mm}$ diameter) optimized for ergonomic hand grip and flush surface stability.
- **Snap-In Connection Mechanics:** The clearance passage between the innermost rims of the side cup holders is restricted to exactly $64\text{mm}$. Pushing a standard $67\text{mm}$ tennis ball downward compresses its rubber wall by $3\text{mm}$. Once pushed past the entry lips to the centerline axis, the ball pops back to its original shape, locking it with a tactile snap fit.
- **Center Support Roller:** A horizontal wheel ($36\text{mm}$ diameter) mounted on a local Y-axis pin inside the floor center. It protrudes slightly out of the base floor to support the ball from underneath, transferring downward body forces away from the side axles.
- **Fingerprint Cups:** Concave side holders featuring a built-in internal spherical offset that creates concentric gripping ridges to latch onto ball fuzz.
- **Concealed Blind Bores:** $18\text{mm}$ deep blind pockets on the inner faces of the arms, ensuring the exterior surface remains smooth to the touch.

## 3. Structural Dimensions (V7.2 Layout)
- **Base:** Cylinder, $120\text{mm}$ diameter ($60\text{mm}$ radius), $15\text{mm}$ thickness.
- **Support Arms:** Integrated into base outer radius ($60\text{mm}$). $22\text{mm}$ thick each, $40\text{mm}$ depth (Y-axis), extended to $85\text{mm}$ height.
- **Arm Cavity (Inner Span):** $82\text{mm}$ wide clear space between arms.
- **Center Roller Cavity:** $40\text{mm} \times 20\text{mm}$ cutout box carved out at $(0,0)$.
- **Center Wheel:** Cylinder, $18\text{mm}$ radius ($36\text{mm}$ diameter), $16\text{mm}$ track width, spinning horizontally.
- **Rotating Cups:** $72\text{mm}$ outer diameter, $25\text{mm}$ base thickness, $33.5\text{mm}$ spherical inner radius profile.
- **Integrated Axle Stubs:** $8\text{mm}$ diameter ($4\text{mm}$ radius), $15\text{mm}$ length, extending outward from cup flat faces.

## 4. Software & CAD Strategy
- **Environment:** FreeCAD (Python Macro Automation).
- **API Workbench:** Pure `Part` primitives (`Part::Cylinder`, `Part::Box`, `Part::Sphere`) and boolean combinations (`Part::Fuse`, `Part::Cut`). No PartDesign workbench dependencies.