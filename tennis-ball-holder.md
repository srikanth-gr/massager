<!-- METADATA_START -->
- **File Name**: tennis-ball-holder.md
- **Version**: 6a44f45
- **Last Commit Date**: 2026-06-03 12:22:07 +0200
- **Last Comment**: V6 design - Round base, blind axle pockets, open-jaw narrow arms.
<!-- METADATA_END -->

# Project Requirements: Shoulder Massage Tennis Ball Holder

## 1. Functional Objective
Design an ergonomic, heavy-duty shoulder massage tool that holds a standard tennis ball. The ball rolls smoothly along a single axis (X-axis) via two rotating concave cups. The external frame is rounded and contour-curved to feel smooth against hands and skin, with completely enclosed hardware channels.

## 2. Mechanical Design & Motion Profile
- **Axis of Rotation:** Single-axis (X-axis).
- **Base Geometry:** Round circular foundation ($120\text{mm}$ diameter) to sit comfortably in the hand or flush against surfaces.
- **Enclosed Axle System:** Blind bores on the arm inner faces. Axle stubs are short ($15\text{mm}$), completely concealed, and do not protrude to the outside face of the arms.
- **Open-Jaw Clearance:** Support arms are narrower ($40\text{mm}$ depth) than the rotating cups ($72\text{mm}$ diameter), ensuring the frame never impedes massage contact.

## 3. Structural Dimensions (V6 Layout)
- **Base:** Cylinder, $120\text{mm}$ diameter ($60\text{mm}$ radius), $15\text{mm}$ thickness.
- **Support Arms:** Integrated into base outer radius ($60\text{mm}$). $22\text{mm}$ thick each, $40\text{mm}$ depth (Y-axis), $70\text{mm}$ total height.
- **Arm Cavity (Inner Span):** $76\text{mm}$ clear space between arms.
- **Blind Bores:** $8.5\text{mm}$ diameter, $18\text{mm}$ deep pockets centered at $Z = 50\text{mm}$.
- **Rotating Cups:** $72\text{mm}$ diameter, $28\text{mm}$ base thickness, $33.5\text{mm}$ spherical inner radius profile.
- **Integrated Axle Stubs:** $8\text{mm}$ diameter, $15\text{mm}$ length, extending outward from cup flat faces.

## 4. Software & CAD Strategy
- **Environment:** FreeCAD (Python Macro Automation).
- **API Workbench:** Pure `Part` primitives (`Part::Cylinder`, `Part::Box`, `Part::Sphere`) and boolean combinations. No PartDesign workbench workflow dependencies.