<!-- METADATA_START -->
<!-- METADATA_END -->
# Project Requirements: Shoulder Massage Tennis Ball Holder

## 1. Functional Objective
The goal is to design a heavy-duty, mechanical shoulder massage tool that holds a standard tennis ball. The device must allow the ball to roll smoothly under load to relieve deep muscle tension, shifting away from a static cup design to a dynamic, low-friction roller system.

## 2. Mechanical Design & Motion Profile
*   **Axis of Rotation:** Single-axis tracking. The ball must spin strictly in place along the horizontal **X-axis** (acting like a wheel/roller) to follow the specific stroke direction of a shoulder massage.
*   **Load-Bearing Architecture:** Over-center yoke design. The support arms extend past the vertical equator (halfway mark) of the ball, creating a physical cradle that traps the ball securely.
*   **Axle Mechanics:** Continuous through-axle channel. Uses a straight horizontal bore (8.4mm diameter) across both arms and the center of the ball. This accommodates an M8 steel bolt or threaded rod, moving 100% of the mechanical pressure off the plastic parts and onto the metal core.

## 3. Structural Integrity & Rigidity
*   **Load Support:** The structure must survive full human body weight pressed against a wall or floor without fracturing, slipping, or delaminating.
*   **Component Dimensions (MVP Layout):**
    *   **Base Footprint:** Thick stabilizing foundation block (110mm x 80mm).
    *   **Base Thickness:** Minimum 15mm solid thickness to eliminate flex under load.
    *   **Support Towers (Yoke):** Reinforced vertical side walls (22mm thickness each).
*   **Ball Cavity:** A central spherical cutout with a 33.5mm radius, optimized to cradle a standard 67mm diameter tennis ball with minimal friction.

## 4. Software & CAD Strategy
*   **Environment:** FreeCAD (Python Macro Automation).
*   **API Compatibility:** Scripted exclusively using `Part` workbench primitives (`Part::Box`, `Part::Cylinder`, `Part::Sphere`) and core boolean operations (`Part::Fuse`, `Part::Cut`). This approach avoids version-specific `PartDesign` workbench dependencies and prevents script crashes across different software builds.

## 5. Design History & Evolution
1.  **V1 (Static Cup):** A single-piece solid cylinder design meant to hold the ball passively. (Superseded to enable ball rolling).
2.  **V2 (Vertical Pin Pivot):** A two-part assembly featuring a base pin and a free-spinning dual-claw arm tracking 360-degree rotation. (Superseded due to load limitations and risk of the ball slipping under body weight).
3.  **V3 (Industrial Over-Center Yoke MVP):** The current heavy-duty design featuring thick 22mm arms and a continuous metal through-bolt along the X-axis for maximum strength and constrained tracking.
