<!-- METADATA_START -->
- **File Name**: tennis-ball-holder.md
- **Version**: da062ef
- **Last Commit Date**: 2026-06-03 14:44:36 +0200
- **Last Comment**: V7.11 design - Fully unified file containing behavioral V&V protocols and programmatic code review gates.
<!-- METADATA_END -->

# Project Requirements: Shoulder Massage Tennis Ball Holder

## 1. Functional Objective
Design an industrial-strength, ergonomic shoulder massage tool holding a standard tennis ball. The device separates vertical compression loads (handled by a dedicated roller wheel) from lateral pop-out loads (handled by side cups). The back of the device must remain entirely flat to sit flush against wall surfaces.

## 2. Mechanical Design & Assembly Profile
- **Solid Continuous Base:** A completely solid $15\text{mm}$ thick circular foundation plate providing uniform structural stiffness.
- **Flush Edge Support Arms:** The support arms have a squat, rigid height of $68\text{mm}$ to prevent bending deflection. Their outer faces are trimmed to stay perfectly flush with the $60\text{mm}$ radius base edge without losing core thickness.
- **Raised Pedestal Housing:** A solid $24\text{mm} \times 32\text{mm} \times 12\text{mm}$ block fused directly to the base floor to house a separate support wheel.

## 3. Ball Cup Holders & Wheel Specifications
- **Ellipsoid Outer Profile:** The rotating side cups feature an organic ellipsoid shape that maximizes material thickness at the equator for high lateral force resistance.
- **Fingerprint Grip Texture:** The inner $33.5\text{mm}$ radius cavity is textured with concentric friction ridges to tightly grab the tennis ball fuzz.
- **Calibrated Snap-In Clearance:** The clearance gap between the inner faces of the cups is exactly $64\text{mm}$ to provide a secure tactile snap-fit on a standard $67\text{mm}$ tennis ball.
- **Standalone Roller Wheel:** A separately printed $12\text{mm}$ diameter, $16\text{mm}$ wide wheel mounted inside the pedestal on a $4\text{mm}$ horizontal pin to allow smooth X-axis ball rotation.

## 4. Structural Dimensions
- **Base Footprint:** Cylinder, $120\text{mm}$ diameter ($60\text{mm}$ radius), $15\text{mm}$ thickness.
- **Support Arms:** $22\text{mm}$ thick, $40\text{mm}$ deep, $68\text{mm}$ high.
- **Ellipsoid Cups:** $72\text{mm}$ major diameter, $25\text{mm}$ absolute base thickness, $33.5\text{mm}$ inner pocket radius.
- **Integrated Axle Stubs:** $8\text{mm}$ diameter ($4\text{mm}$ radius), $15\text{mm}$ length, fitting within $18\text{mm}$ blind pockets on the inner arms.

## 5. Functional Verification & Validation (V&V) Protocol

This protocol focuses on verifying structural behavior, component integration, and mechanical function rather than rigid dimensional measurements. All checks must be performed to guarantee user safety and smooth operation under heavy massage loads.

### Phase 1: Standalone Component Verification
- **Base Foundation Integrity:** Verify the primary base plate back surface is completely flat and unbroken. It must lay 100% flush against a wall or floor without rocking, ensuring stability during use.
- **Support Arm Rigidity:** Manually stress-test the squat support arms before assembly. They must feel completely rigid with zero flex or structural deflection under hand pressure.
- **Cup Geometry Inspection:** Verify the exterior ellipsoid profile tapers smoothly toward the poles while maintaining a thick, robust mass around the equator line to prevent structural splitting.
- **Lower Support Wheel Rotation:** Ensure the standalone 12mm wheel spins freely on its central bore axis before it is placed into the pedestal housing.

### Phase 2: Built-in Integration & Assembly Verification
- **Pedestal Clearance:** Once the support wheel is dropped into the pedestal housing and pinned along the horizontal Y-axis, verify that it rotates smoothly with zero binding against the internal side walls.
- **Concealed Axle Fitment:** Verify that the side cup stubs insert fully into the blind pockets of the arms. The stubs must fit securely without sliding out laterally, while allowing the cups to rotate smoothly.
- **Ergonomic Surface Check:** Feel all exposed borders, seam lines, and the front arc-cut profiles of the arms. All edges must be smooth to the touch, with no sharp steps or 3D printing burrs.

### Phase 3: Overall System Functional Validation
- **Tennis Ball Retention (Static Function):** Push a standard 67mm tennis ball into the frame. It must pass through the cup rims with a distinct, positive mechanical snap-fit and remain held securely without falling out when the holder is inverted or shaken.
- **Grip & Traction Performance:** The ball fuzz must engage fully with the internal concentric fingerprint-like friction ridges of the ellipsoid cups, providing predictable mechanical resistance.
- **True Axial Rotation (Dynamic Function):** Apply full body-weight compression force to the tennis ball and rotate it along the X-axis. The ball must spin fluidly, riding directly on the lower tangent roller wheel while the cups seamlessly guide its orientation.

### Phase 4: Code Submission Review Gates
Before saving, executing, or committing any new FreeCAD Python macro scripts to this repository, verify that the source code satisfies these programmatic safety guidelines:
- [ ] **Chassis Strength Protection:** Ensure that no `Part::Cut` or boolean subtraction tools pierce or intersect the bottom $Z = 0$ plane of the base plate. The underside must remain an absolute solid plane.
- [ ] **Sturdiness Optimization:** Confirm the arm height variables do not exceed $68\text{mm}$ to prevent turning the pillars into fragile levers that could snap under heavy body-weight compression.
- [ ] **Component Separation:** Verify that the script instantiates the `CenterWheel`, `LeftCup`, and `RightCup` objects as distinct topological entities separated from the main unified base yoke, preventing them from fusing together during generation.
- [ ] **Motion Dynamics Separation:** Confirm that the macro keeps rotation constraints isolated. The lower support wheel must be programmatically independent to rotate strictly on its horizontal Y-axis pin for X-axis ball travel, while the left and right cups are isolated as independent, free-spinning side-guides to prevent binding.

## 6. CAD Implementation Architecture Notes (Lessons Learned)

To prevent breaking geometry during future programmatic modifications or scaling changes, the FreeCAD script must adhere to the following architectural constraints discovered during development:

### 1. Avoid Thin-Sliver Arm Geometry (The Intersection Bug)
- **The Error:** Initially, cutting the support arms using `Part::Common` with a cylinder the exact diameter of the base caused the front and back corners of the arm blocks to shear off completely. This left structurally useless, paper-thin wall slivers.
- **The Geometric Fix:** The arm blocks must be artificially inflated along the X-axis (`arm_thickness + 10.0`) so they completely cross the base circle boundary. A custom negative cookie-cutter mold (`ArmTrimmingTool`) is then built by subtracting a base-radius cylinder from a larger box volume. Performing a `Part::Cut` with this inverted mask removes only the overhanging exterior corner ears, preserving 100% of the structural wall thickness.

### 2. Non-Uniform Primitive Scaling (The AttributeError Bug)
- **The Error:** Attempting to assign a non-uniform scale directly to an active feature primitive property (e.g., `left_sph.Scale = (0.7, 1.0, 1.0)`) throws a Python interpreter `AttributeError`. Standard FreeCAD `Part` primitives do not expose a mutable scaling property.
- **The Geometric Fix:** Ellipsoids must be generated at the pure topological shape level before being wrapped into a document feature. The script instantiates a basic shape using `Part.makeSphere()`, creates a geometric matrix transformation object (`App.Matrix4x4()`), applies `.scale(x, y, z)` to the matrix, transforms the underlying shape via `.transformShape()`, and only then binds the resulting unique shape to a generic `Part::Feature`.