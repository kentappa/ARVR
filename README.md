# Baja ATV / Pine Ridge

Open this folder in Unity Hub with Unity **6000.5.6f1**, then open `Assets/Baja/Generated/BajaDemo.unity` and press Play. Double-click the Game tab to enlarge the view.

## Configure, then drive

The scene starts in a 3D vehicle configurator. Drag in the centre of the view to orbit and use the mouse wheel to zoom. Click the markers on the vehicle or the Suspension, Tyres and Paint tabs to choose parts and a metallic body colour. Click **Choose Terrain**, select a map, then click **Drive** to release the vehicle. Stop below 1 km/h and press Tab to reopen the configurator.

| Controls | Action |
| --- | --- |
| W / S or Up / Down | Drive, brake, reverse |
| A / D or Left / Right | Steer |
| Space | Brake |
| R | Recover to the starting clearing |
| C | Cycle driving cameras |
| Tab | Open or close the configurator |

## Environment and vehicle

The 300 x 300 metre procedural landscape includes rolling hills, a winding dirt trail, pine trees, granite outcrops, amber trail markers, atmospheric fog and soft sunlight. Trees and rocks have colliders. Follow the marked trail for the gentlest route; the surrounding hills are steeper. Invisible boundaries keep the vehicle inside the generated landscape.

The ATV has shaped body panels, metallic paint, a roof canopy, racing graphics, harness straps, LED-style lights, a radiator grille, cooling fins, wheel hubs and bolts. It retains three suspension assemblies and three tyre tread variants. This is stylized procedural art, not a photorealistic CAD vehicle or an engineering-validated dynamics simulation. Lights use emissive materials; no post-processing bloom is installed. Tyre grip is a global coefficient rather than a surface-specific mud simulation. Decorative wishbones do not articulate.

## Editing

`Assets/Baja/Generated/BajaATV.prefab` contains the vehicle. Runtime code lives in `Assets/Baja/Scripts`; scene, terrain and art generators live in `Assets/Baja/Editor`. The project uses the built-in render pipeline and legacy Input Manager.

**Baja > Create demo scene** regenerates the scene and vehicle prefab, replacing generated content. Save hand-edited scenes or prefabs under other names before using it. Paint and part selections are session-only.

## Checks

The validation runner checks wheel grounding, acceleration, braking, part swaps, trail collision and configurator physics locking. Shader appearance, orbit controls and the final GUI also need inspection in Play mode. See the latest run log for the completed checks; validation code existing in the project does not itself confirm that a run passed.

## Exploded inspection (video reference)

The opening configurator now separates the visual parts while preserving the WheelCollider mounts. Suspension mode lifts the coilovers and moves the wheels aside; tyre mode spreads the wheel assemblies farther out. The roof and outer panels lift to expose the chassis. Gold guide lines connect the assemblies to their fitted positions, with an inspection ring beneath the ATV.

Hover over the Suspension or Tyres tabs, part options, or vehicle markers to show the exploded view. Move the pointer away to reassemble. Clicking still selects or fits a part; hovering does not change the fitted parts. Use the **Part Separation** slider to adjust the spacing. Paint mode temporarily reassembles the body. **Choose Terrain** first returns the parts to position, then opens map selection; **Drive** restores driving physics. Part choices apply to all four corners. This is a desktop adaptation of the video's layered inspection interaction, not hand-tracked VR.

Exploded-view validation passed in Unity 6000.5.6f1: visual wheel separation, unchanged collider mounts, reassembly input lock, and restoration of driving physics.


## Terrain selection

After configuring the ATV, choose **Choose Terrain**. The vehicle reassembles and remains stationary while you choose **Pine Ridge**, **Sand Dunes**, or **Highway**. Use **Back to Vehicle** to keep adjusting your ATV, or the **Drive** button to enter the selected map. Suspension, tyres and paint are retained across maps. Only the selected map's geometry and colliders are active.

- **Pine Ridge:** original hills and forest, plus 22 alternating trail rocks and seven fallen logs. The starting clearing remains unobstructed.
- **Sand Dunes:** a 300-metre desert with rolling dune crests and a flat starting clearing. This uses the existing tyre physics, without deformable sand.
- **Highway:** a bounded 288-metre straight road with asphalt, four lanes, centre and edge markings, guardrails and end barriers. There is no traffic simulation.

Reopen configuration with Tab while stopped to choose a different map. R returns to the selected map's starting point.

Validated on 15 October 2026 in Unity 6000.5.6f1: vehicle acceleration/braking, part swaps, hover separation/reassembly, exclusive terrain activation, retained part selection, and four-wheel grounding on all three maps passed. The configuration-to-selection flow and desert/highway dashboard views were also inspected in Play mode. Run details are in `terrain-final.log`.
