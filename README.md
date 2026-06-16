# Nukxon Exporter for Unreal Engine

Turn your Unreal Engine scenes into walkable, photoreal VR tours. Place camera hotspots in your level, hit export, and Nukxon packages your scene into a single `.nukxon` file for the Nukxon web viewer.

- 360 degree panoramas captured with Lumen, offscreen through Movie Render Queue
- Scene mesh export
- No code, runs entirely in the editor

## Requirements

- Unreal Engine 5.7
- Windows 64-bit
- Movie Render Pipeline plugin (ships with the engine; enabled automatically as a dependency)

## Installation

### From Fab (Epic Games Launcher)
1. Open the Epic Games Launcher and find Nukxon Exporter in your Fab library.
2. Click "Install to Engine" and choose Unreal Engine 5.7.
3. Open your project. The plugin is enabled automatically.

### Manual
1. Extract the plugin into `YourProject/Plugins/NukxonExporter/`.
2. Restart the editor.
3. If it is not already on, enable "Nukxon Exporter" under Edit > Plugins, then restart.

You will know it loaded when the **Nukxon** button appears in the Level Editor toolbar, next to the Play button.

## Quick start

1. Click the **Nukxon** button in the toolbar to open the Nukxon Exporter panel.
2. In **Scene Setup**, leave the engine on Lumen and pick a quality. Use "Set From View" to set the entry view from your current viewport.
3. In **Hotspots**, click **Place Hotspot**, then click surfaces in the level to drop a viewpoint anywhere you want a visitor to stand.
4. In **Output**, choose a folder and click **Export .nukxon**.
5. Open the `.nukxon` in the Nukxon viewer to walk the space in any browser.

## Panel reference

### Scene Setup
- **Engine**: Lumen. Panoramas are captured with your scene's own Lumen lighting.
- **Quality**: Standard (2048 per face) for final exports, or Draft (1024) for quick tests.
- **Mesh**: choose what geometry to export (the full visible scene by default).
- **Default Camera**: the hotspot the tour opens on. Click **Set From View** to capture your current viewport framing as the entry view, and **Preview Start** to jump the viewport to that entry view and check it.

### Hotspots
- **Place Hotspot**: enters placement mode. Click surfaces in the viewport to drop hotspots. Each one becomes a full 360 degree viewpoint in the tour.
- **Top / Perspective**: toggle a top-down view to plan coverage.
- **Graph**: show or hide the line-of-sight graph between hotspots, which helps you plan navigation and spot gaps.
- Each row lets you select the hotspot in the editor or delete it. You can place up to 100 hotspots per scene.

### Teleport Points
- **Add**: creates a teleport menu entry. Set its label and pick which hotspot it points to. These become the named navigation menu in the viewer (for example "Kitchen", "Living Room").
- Use the up and down arrows to reorder, and remove to delete an entry.

### Glass (optional)
- Select one or more glass actors in the viewport, then click **Mark Selected as Glass** to tag them so they are exported correctly. **Clear** removes all tags. Each row can be selected in the viewport or untagged.

### Anchors (optional)
- **Place Anchor**: drops a spatial marker at your cursor's aim point. Aim at a doorway or boundary in the viewport and click. The Nukxon platform uses anchors to connect this project to others, for example multi-floor builds.

### Output
- Choose an output folder, then **Export .nukxon**. The plugin renders each hotspot's panorama offscreen through Movie Render Queue and packages the panoramas, the scene mesh, and a manifest into a single `.nukxon` file. It never takes over your viewport.

## Viewing your tour

Open the exported `.nukxon` in the Nukxon viewer to walk the space in any web browser. No install or signup is needed to view a shared tour.

## Troubleshooting

**Visible seams between panorama faces.** This is almost always auto-exposure, where each face adapts to a different brightness. Use a fixed (manual) exposure in your scene. The plugin runs a pre-flight check and warns you if auto-exposure is enabled before you export.

**The Nukxon button is not in the toolbar.** Confirm you are on Unreal Engine 5.7 and that "Nukxon Exporter" is enabled under Edit > Plugins, then restart the editor.

## Support

Email contact@nukxon.com or visit https://nukxon.com.

## License and third-party software

Distributed via Fab under the standard Fab license. The plugin bundles two third-party libraries:

- libwebp (BSD-3-Clause, Google) for WebP encoding of the panorama faces
- Draco (Apache-2.0, Google) for mesh compression

License texts are included in the plugin's `ThirdParty/` folder.
