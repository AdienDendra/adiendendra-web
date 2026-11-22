---
title: "AD Skin Tool Documentation & Tutorials"
translationKey: "ad-skin-tool-tutorial"
summary: "A guide to AD Skin Tool workflows in Autodesk Maya."
description: "How to load meshes, manage influences, bind, flood, smooth, visualise, mirror, and transfer skin weights with AD Skin Tool."
date: 2026-09-11T10:00:00+10:00
lastmod: 2026-10-06T22:23:00+11:00
tags: ["maya", "ad-skin-tool", "documentation", "tutorial"]
categories: ["documentation"]
comments: true
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

This guide walks through the controls in AD Skin Tool and explains how each one affects your Maya scene.

For pricing, compatibility, and release availability, visit the [AD Skin Tool product page](/en/3dtools/ad-skin-tool/).

## Install and open the tool

Download the package built for the required Maya version, operating system, and processor architecture. Follow the installation instructions included in the ZIP; each build targets a specific Maya version and platform.

For the v1.0.0 download, open a Python tab in Maya’s **Script Editor** and run the command from step 5 of the ZIP’s `README.txt`. For packages with an `ad_skin_tool` folder, use:

```python
from ad_skin_tool import launch

launch.show(
    reload=False,
    auto_refresh=False,
)
```

AD Skin Tool opens as a dockable Maya panel and can also be left floating. **Tool Help** provides a quick reference and environment diagnostics. **License** provides controls for starting a trial, activating a licence, and managing devices. See the [AD Skin Tool License Guide](/en/documentation/ad-skin-tool-license/) for the complete customer workflow.

## Recommended workflow

1. Select a polygon mesh or one of its components, then click **Load Mesh**.
2. Add or select the required joints in **Joints / Influences**.
3. Set **Blend** and **Iterations** for the next operation.
4. Use **Bind Skin**, **Add Influence**, **Flood**, or **Smooth** for the loaded mesh.
5. Use the separate **Mirror** and **Transfer** utilities when those workflows are required.
6. Read the status message after every operation. Detailed diagnostics are also printed in Maya's Script Editor.

> The current selection in Maya affects what each operation does. Before running a command, check whether the selection contains the loaded mesh, components, joints, or nothing.

## Mesh / Skin Context

### Load Mesh

Select a polygon mesh, or any of its vertices, edges, or faces, then click **Load Mesh**. The mesh remains active in AD Skin Tool even when the Maya selection changes. To switch meshes, select another mesh and click **Load Mesh** again.

The panel shows:

- **Skin Cluster:** the skinCluster attached to the loaded mesh, or `<no skinCluster>` when the mesh is unskinned.
- **Loaded Mesh:** the name of the transform currently used by the Bind, Add Influence, Flood, Smooth, and visualisation workflows.
- **Listed Joints:** the number of bind and pending joints currently shown in the influence list.

Loading a skinned mesh automatically displays its existing influences in the joint list. For an unskinned mesh, the list starts empty so joints can be added before binding.

{{< collapse title="Load Mesh demonstration" collapse="true">}}
![Load Mesh demonstration](/images/documentation/ad-skin-tool/01-load-mesh.gif)
{{< /collapse >}}

## Joints / Influences

### Bind and pending joints

The list can contain two types of joint:

- A **bind influence** already belongs to the loaded skinCluster and is displayed in green.
- A **pending joint** exists in the scene and in the list but has not yet been added to the loaded skinCluster. It is displayed in white.

Select one or more joints in Maya and click **Add Joints To The List**. On an unskinned mesh, these joints will be used by **Bind Skin**. On a mesh with an existing skinCluster, new joints remain pending until selected in the list and processed with **Add Influence**.

To find a joint in a long influence list, select it in Maya and click **Select Joints In The List**. The matching rows will be highlighted.

### Sort, Search, and Pin

- **A to Z** and **Z to A** sort the displayed joint names.
- **Pending Joints** moves pending joints to the top of the list and is available only when pending joints exist.
- **Search** filters the visible rows without changing the skinCluster.
- **Pin** keeps only the selected rows visible. Select the required joint rows first, then click the pin icon. Disable Pin to restore the normal filtered list.
- **Reset** clears the loaded mesh context, joint list, search, pin, and smoothing settings in the tool.

### Lock and context menu actions

Click the lock icon beside a joint to lock or unlock it. For bound influences, this changes the skinCluster's influence lock. For pending joints, the lock state is kept in AD Skin Tool until the joint is added.

Right click the joint list for additional actions:

- Lock or unlock selected rows, or the inverse selection.
- Select all pending joints.
- Remove selected, inverse selected, or all pending joints. These removal commands do not remove bind influences.
- Select vertices that have non-zero weight from the selected bind influences.
- Select one or all listed joints in the Maya scene.
- Set one selected joint as **Global Owner**, or clear the current Global Owner.

**Global Owner** is optional. For a mesh with detached secondary regions, a specific joint can be assigned as their owner after the usual local assignment in Bind, Add Influence, or Flood. Most meshes won't need this; leave it unset when the automatic result is already correct. The active Global Owner is highlighted in yellow and applies only to the loaded mesh.

{{< collapse title="Joint List demonstration" collapse="true">}}
![Joint List demonstration](/images/documentation/ad-skin-tool/02-joint-list.gif)
{{< /collapse >}}

## Blend and Iterations

These controls are shared by **Bind Skin**, **Add Influence**, **Flood**, and **Smooth**:

- **Blend** ranges from `0.000` to `1.000` and controls how strongly each smoothing pass shifts weights based on neighbouring vertices. Lower values preserve more of the current blocking; higher values produce a stronger smoothing effect.
- **Iterations** ranges from `0` to `10`. More iterations spread and relax the result farther through neighbouring vertices.

For Bind Skin, Add Influence, and Flood, **Iterations 0** keeps the result in hard blocking mode. **Smooth** requires Iterations `1` or higher. The default values are Blend `0.250` and Iterations `0`.

## Bind Skin

Use **Bind Skin** when the loaded mesh does not have a skinCluster yet.

1. Load an unskinned polygon mesh.
2. Add at least two joints to the list.
3. Optionally set a Global Owner.
4. Choose Blend and Iterations. Use Iterations `0` for a hard initial blocking result, or a positive value to include smoothing.
5. Click **Bind Skin** and wait for the operation to finish.

Bind Skin uses the **entire joint list**, not just the highlighted rows. It works out which surface regions belong to each joint, creates a skinCluster, writes the weights, and updates the list to show the newly bound influences.

{{< collapse title="Bind Skin demonstration" collapse="true">}}
![Bind Skin demonstration](/images/documentation/ad-skin-tool/03-bind-skin.gif)
{{< /collapse >}}

## Add Influence

Use **Add Influence** to add joints to an existing skinCluster and assign weights to their local surface regions.

1. Select the new joints in Maya and click **Add Joints To The List**.
2. In the influence list, select the pending joints to add.
3. Make sure those pending rows are unlocked.
4. Set Blend and Iterations.
5. Click **Add Influence**.

Only the selected pending joints are added. Existing influences stay in the skinCluster while the new joints receive their local regions. Once the operation finishes, those joints appear as bound influences and remain selected in the list.

{{< collapse title="Add Influence demonstration" collapse="true">}}
![Add Influence demonstration](/images/documentation/ad-skin-tool/04-add-influence.gif)
{{< /collapse >}}


## Flood

**Flood** recalculates the weight regions for the selected joints. Those joints must already be bound influences.

1. Select one or more joints that are already bind influences in the UI list.
2. In the Maya scene, select vertices, edges, or faces on the loaded mesh for a component operation. To process the whole mesh, select the loaded mesh object.
3. Set Blend and Iterations.
4. Click **Flood**.

With components selected, Flood works within that component scope. Maya Soft Selection is supported too, and its falloff affects the result. If the loaded mesh object is selected instead, AD Skin Tool asks for confirmation before processing the whole mesh.

With Iterations `0`, Flood produces a hard-blocked result. Set Iterations above `0` to smooth the affected region using the current Blend value. Pending joints are ignored, even if they are selected alongside bound influences—use Add Influence to add them first. The selected Flood targets must be unlocked; weights on other locked influences stay protected.

{{< collapse title="Flood demonstration" collapse="true">}}
![Flood demonstration](/images/documentation/ad-skin-tool/05-flood.gif)
{{< /collapse >}}

## Smooth

**Smooth** relaxes the existing skin weights on selected components or across the whole loaded mesh.

1. In Maya, select vertices, edges, or faces on the loaded mesh. To smooth the whole mesh, select the loaded mesh object.
2. Set Blend and set Iterations to `1` or higher.
3. Click **Smooth**.

Smooth does not require a joint row to be selected. Component mode respects Maya Soft Selection falloff. Object mode displays a confirmation before processing. Locked influence values remain unchanged, and vertices with no writable weight are skipped.

{{< collapse title="Smooth demonstration" collapse="true">}}
![Smooth demonstration](/images/documentation/ad-skin-tool/06-smooth.gif)
{{< /collapse >}}

## Skin Weight Visual

Skin Weight Visual displays one bind influence's weights directly on the loaded mesh without changing the stored skin weights.

1. Load a mesh with an existing skinCluster.
2. Select exactly one bind influence in the list.
3. Choose a display mode:
   - **Spectrum:** black, blue, green, yellow, orange, red, and white.
   - **Heat:** black, red, orange, yellow, and white.
   - **Grayscale:** black through grey to white.
4. Choose **Off** to restore normal mesh shading.

With **Live Joint Selection** set to **On**, selecting a listed bind joint in the Maya scene also highlights it in the UI list and refreshes the active weight visual. Set it to **Off** to keep the displayed influence fixed while the Maya scene selection changes.

The visual refreshes after relevant weight operations, Undo, and Redo. This is only a temporary viewport display; it does not bake colour data into the skin weights.

{{< collapse title="Skin Weight Visual demonstration" collapse="true">}}
![Skin Weight Visual demonstration](/images/documentation/ad-skin-tool/07-skin-weight-visual.gif)
{{< /collapse >}}

## Mirror Skin Weights Posed Mesh

**Mirror** stores vertex pairs so weights can be mirrored even when a skinned character is posed. When bind-reference geometry is available, the pairing is built from that geometry, so the character does not need to be returned to its bind pose.

### Register the mirror pairing

1. Select the mesh to mirror and click **Load Mirror Mesh**. This context is separate from the main Load Mesh context.
2. Choose the symmetry plane:
   - **YZ** mirrors across X.
   - **XZ** mirrors across Y.
   - **XY** mirrors across Z.
3. Choose the source-to-target **Direction** for that axis.
4. Set the centre plane coordinate. Enter the value directly, or select suitable centre components or the mesh transform and click **Register Selected** to calculate it from the selection.
5. Set **Tolerance**. Start with the default `0.001`; increase it only enough to resolve valid symmetrical counterparts.
6. Enter literal **Left** and **Right** joint name markers, for example `L` / `R`, `L_` / `R_`, or `_l` / `_r`. The markers may be prefixes, suffixes, or infixes, but they must be different.
7. Click **Preview Pairing**.

Preview reports valid pairs, centre vertices, unmatched or ambiguous vertices, and the maximum pairing error. Vertices that need attention are selected in Maya for inspection. Preview does not overwrite an existing pairing.

Once the preview looks valid, click **Register Pairing**. The pairs are stored on the mesh and can be reused. If a pairing already exists, the button changes to **Replace Pairing...** and asks for confirmation. After a topology change, run Preview again and replace the old pairing.

### Apply mirrored weights

1. Load a mirror mesh with an existing valid registered pairing and skinCluster.
2. Set Direction and confirm the Left/Right markers.
3. For mesh mode, leave mesh components unselected or select the complete registered region.
4. For component selection mode, select donor components from one side only. Their registered counterparts become the targets.
5. Click **Mirror Skin Weights**.

The selected direction controls which side donates weights. Joint influences are paired from the literal Left/Right markers. Locked target influence values are preserved. Do not select both sides of the same mirror region in component mode.

The Mirror **Reset** button clears the active Mirror Mesh and current UI options. It does not delete a persistent pairing already stored on the mesh.

{{< collapse title="Mirror demonstration" collapse="true">}}
![Mirror demonstration](/images/documentation/ad-skin-tool/08-mirror-optimized.gif)
{{< /collapse >}}

## Transfer Skin Weights

**Transfer** projects skin weights from one or more skinned source meshes onto one or more targets. The registered sources provide the reference influences and weights; the targets receive them.

### Register sources and targets

1. Select one or more skinned source meshes and click **Add Selected** under **Sources**. Component selection is supported, but AD Skin Tool registers the full source mesh as the donor.
2. Select one or more target meshes or their components and click **Add Selected** under **Targets**. The target meshes are registered immediately; component selection is evaluated later when Preview Transfer runs.
3. Use **Remove Selected** or **Clear** to edit either list. A mesh cannot be registered as both a source and a target.

Right click either list to select the highlighted object or every registered object in that list within the Maya scene.

### Understand target scope

The registered Target list determines which meshes participate. The Maya component selection when Preview runs overrides the scope only for matching registered targets:

| Target state at Preview | Resulting scope |
|---|---|
| No components selected on a registered target | The entire target mesh is processed |
| Components selected on a registered skinned target | Only the selected target vertices are processed |
| Components selected on an unskinned target | That component target is skipped and must be bound first |
| Unskinned target used as a whole object | A new target skinCluster can be created during Apply |

Component and object modes can be combined in a single transfer. For example, one registered target can use selected vertices while another uses its entire mesh. Selecting components on an unregistered mesh does not add that mesh to the transfer.

### Preview and apply

1. Set the intended target component selection, or leave registered targets without selected components for object mode.
2. Click **Preview Transfer**.
3. Review the status summary: registered, active, and skipped targets; requested and writable vertices; locked or empty rows; and maximum source distance.
4. If the preview is valid, click **Transfer Skin Weights**.

Preview finds the closest source correspondence for each target and saves those matches for Apply. It does not change any weights. If the source or target lists, selected components, skinCluster, or influence order change afterwards, run Preview again before applying.

During Apply:

- An unskinned target in object mode receives a new skinCluster.
- Missing source influences on an existing target are listed before they are added.
- Locked target influences are listed and skipped so their values remain unchanged.
- If missing or locked influences need confirmation, the tool shows **Cancel** and **Proceed**. Cancel keeps the Preview available and makes no changes.
- Transfer and adaptive boundary smoothing run as one operation. If a multi-target transfer fails, the changes are rolled back to avoid a partial result.

The Transfer **Reset** button clears the registered Source and Target lists and the current Preview. It does not reverse a transfer that has already been applied; use Maya Undo for that.

{{< collapse title="Transfer demonstration" collapse="true">}}
![Transfer demonstration](/images/documentation/ad-skin-tool/09-transfer-optimized.gif)
{{< /collapse >}}


## Status, Undo, and diagnostics

Each operation displays a short result beneath its section and prints a more detailed report in Maya's Script Editor. Read both when a Preview is partial or when vertices are skipped because of locks, missing writable donor weight, unmatched geometry, or an invalid component scope.

Applied Bind, Add Influence, Flood, Smooth, Mirror, and Transfer operations participate in Maya's Undo workflow. If the result differs from the expected outcome, use Maya Undo before making further edits.

For support, open **Tool Help**, click **Copy Diagnostics**, and include the copied environment report with a concise description of the problem. Do not include confidential production assets or a complete licence key. Support is available at [hello@adiendendra.com](mailto:hello@adiendendra.com).
