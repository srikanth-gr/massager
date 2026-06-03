<!-- METADATA_START -->
- **File Name**: tennis-ball-holder.md
- **Version**: 6a44f45
- **Last Commit Date**: 2026-06-03 12:22:07 +0200
- **Last Comment**: V6 design - Round base, blind axle pockets, open-jaw narrow arms.

# Project Requirements: Shoulder Massage Tennis Ball Holder

## 1. Functional Objective
Design an industrial-strength shoulder massage tool holding a standard tennis ball. The device is optimized for heavy load-bearing applications by separating vertical and lateral mechanical forces. The $15\text{mm}$ primary base plate remains solid and unbroken to ensure high stiffness.

## 2. Mechanical Design & Assembly Profile (V7.5 Layout)
- **Solid Continuous Base:** The base foundation remains a complete, solid $15\text{mm}$ thick disc for maximum tensile and compressive strength.
- **2x Proportional Raised Pedestal:** A $24\text{mm} \times 32\text{mm} \times 12\text{mm}$ structural housing block is fused directly onto the top face of the base. This provides walls exactly twice the thickness of the wheel radius, keeping the assembly rugged under heavy massage forces.
- **Separate Print Support Wheel:** A $12\text{mm}$ diameter, $16\text{mm}$ wide tangent wheel is printed as a standalone component. It sits inside the pedestal channel on a horizontal Y-axis pin (using a standard $4\text{mm}$ filament snippet or metal rod) to ensure ultra-low friction rotation.
- **Calibrated Snap-Fit Opening:** The clearance passage between the faces of the cup holders is exactly $64\text{mm}$ to provide a firm, tactile snap lock on a standard $67\text{mm}$ tennis ball.

## 3. Structural Dimensions
- **Base:** Cylinder, $120\text{mm}$ diameter ($60\text{mm}$ radius), $15\text{mm}$ thickness.
- **Support Arms:** $22\text{mm}$ thickness, $40\text{mm}$ depth, $85\text{mm}$ height, outer edge curved to $R=60\text{mm}$.
- **Support Wheel (Printed Separately):** $6\text{mm}$ radius ($12\text{mm}$ diameter), $16\text{mm}$ width, $4.2\text{mm}$ center pin bore hole.
- **Pedestal Block Assembly:** Outside envelope of $24\text{mm} \times 32\text{mm} \times 12\text{mm}$ with a $18\text{mm} \times 18\text{mm}$ internal drop pocket.

## 4. Software & CAD Strategy
- **Environment:** FreeCAD (Python Macro Automation).
- **API Workbench:** Pure `Part` primitives (`Part::Cylinder`, `Part::Box`, `Part::Sphere`) and boolean combinations (`Part::Fuse`, `Part::Cut`). No PartDesign workbench dependencies.