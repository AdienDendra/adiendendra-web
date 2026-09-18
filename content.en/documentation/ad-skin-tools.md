---
title: "AD Skin Tools Documentation & Tutorials"
translationKey: "ad-skin-tools-getting-started"
summary: "A guide to AD Skin Tools workflows in Autodesk Maya."
description: "How to load meshes, manage influences, bind, flood, smooth, visualise, mirror, and transfer skin weights with AD Skin Tools."
date: 2026-09-11T10:00:00+10:00
lastmod: 2026-09-11T20:30:00+10:00
tags: ["maya", "ad-skin-tools", "documentation", "tutorial"]
categories: ["documentation"]
comments: false
showToc: true
TocOpen: true
ShowReadingTime: false
ShowPostNavLinks: false
---

This tutorial follows the AD Skin Weights Tool from top to bottom and explains how each control affects the current Maya scene.

For pricing, compatibility, and release availability, visit the [AD Skin Tools product page](/en/3dtools/ad-skin-tools/).

## Install and open the tool

Use the download that matches your Autodesk Maya version, operating system, and processor architecture. Extract the package according to the included installation instructions. Each package is built specifically for its Maya version and target operating system.

Open Maya's **Script Editor**, then switch to a Python tab and run:

```python
import ad_skin_tools.launch as ad_skin_tools

ad_skin_tools.show(
    reload=False,
    auto_refresh=False,
)
```

The tool opens as a Maya workspace control and can be docked or left floating. **Tool Help** opens a compact reference and environment diagnostics. **License** opens the trial, activation, and device management window.

## Recommended workflow

1. Select a polygon mesh or one of its components, then click **Load Mesh**.
2. Add or select the required joints in **Joints / Influences**.
3. Set **Blend** and **Iterations** for the operation you are about to run.
4. Use **Bind Skin**, **Add Influence**, **Flood**, or **Smooth** for the loaded mesh.
5. Use the separate **Mirror** and **Transfer** utilities when those workflows are required.
6. Read the status message after every operation. Detailed diagnostics are also printed in Maya's Script Editor.

> Maya selection is intentionally meaningful. Before running an operation, check whether you have selected the loaded object, components, joints, or nothing at all.

## Mesh / Skin Context

### Load Mesh

Select one polygon mesh, or vertices, edges, or faces belonging to it, then click **Load Mesh**. The tool records that mesh as the working context. Changing the Maya selection afterwards does not replace the loaded context. To work on a different mesh, select it and click **Load Mesh** again.

The panel reports:

- **Skin Cluster:** the skinCluster attached to the loaded mesh, or `<no skinCluster>` when the mesh is unskinned.
- **Loaded Mesh:** the name of the transform currently used by the Bind, Add Influence, Flood, Smooth, and visualisation workflows.
- **Listed Joints:** the number of bind and pending joints currently shown in the influence list.

Loading a skinned mesh automatically populates the list with its existing influences. Loading an unskinned mesh creates an empty working context ready for joints to be added before binding.

{{< collapse title="Load Mesh demonstration" collapse="true">}}
![Load Mesh demonstration](/images/documentation/ad-skin-tools/01-load-mesh.gif)
{{< /collapse >}}

## Joints / Influences

### Bind and pending joints

The list can contain two types of joint:

- A **bind influence** already belongs to the loaded skinCluster and is displayed in green.
- A **pending joint** exists in the scene and in the list but has not yet been added to the loaded skinCluster. It is displayed in white.

Select one or more joints in Maya and click **Add Joints To The List**. On an unskinned loaded mesh, these joints become the set used by **Bind Skin**. On a skinned loaded mesh, newly listed joints remain pending until they are selected in the list and processed with **Add Influence**.

Select joints in the Maya scene and click **Select Joints In The List** to find and highlight their corresponding rows. This is useful when working with a long influence list in the tool window.

### Sort, Search, and Pin

- **A to Z** and **Z to A** sort the displayed joint names.
- **Pending Joints** moves pending joints to the top of the list and is available only when pending joints exist.
- **Search** filters the visible rows without changing the skinCluster.
- **Pin** keeps only the selected rows visible. Select the required joint rows first, then click the pin icon. Disable Pin to restore the normal filtered list.
- **Reset** clears the loaded mesh context, joint list, search, pin, and smoothing settings in the tool.

### Lock and context menu actions

Click the lock control on a row to lock or unlock that joint. For bind influences this follows the skinCluster's influence lock; for pending joints it stages the lock state inside the tool.

Right click the joint list for additional actions:

- Lock or unlock selected rows, or the inverse selection.
- Select all pending joints.
- Remove selected, inverse selected, or all pending joints. These removal commands do not remove bind influences.
- Select vertices that have non-zero weight from the selected bind influences.
- Select one or all listed joints in the Maya scene.
- Set one selected joint as **Global Owner**, or clear the current Global Owner.

**Global Owner** is optional. It provides an explicit owner for detached secondary regions after the conservative local assignment used by Bind, Add Influence, and Flood. Leave it unset when the normal local assignment already gives the intended result. The active Global Owner is highlighted in yellow and belongs only to the currently loaded mesh context.

{{< collapse title="Joint List demonstration" collapse="true">}}
![Joint List demonstration](/images/documentation/ad-skin-tools/02-joint-list.gif)
{{< /collapse >}}

## Blend and Iterations

These controls are shared by **Bind Skin**, **Add Influence**, **Flood**, and **Smooth**:

- **Blend** ranges from `0.000` to `1.000` and controls how strongly each smoothing pass shifts weights based on neighbouring vertices. Lower values preserve more of the current blocking; higher values produce a stronger smoothing effect.
- **Iterations** ranges from `0` to `10`. More iterations spread and relax the result farther through neighbouring vertices.

For Bind Skin, Add Influence, and Flood, **Iterations 0** keeps the result in hard blocking mode. **Smooth** requires Iterations `1` or higher. The default values are Blend `0.250` and Iterations `0`.

## Bind Skin

Use **Bind Skin** to create the initial skinCluster on an unskinned loaded mesh.

1. Load an unskinned polygon mesh.
2. Add at least two joints to the list.
3. Optionally set a Global Owner.
4. Choose Blend and Iterations. Use Iterations `0` for a hard initial blocking result, or a positive value to include smoothing.
5. Click **Bind Skin** and wait for the operation to finish.

Bind Skin uses the **entire joint list**, not only the highlighted rows. It calculates the natural surface ownership for the listed joints, creates one skinCluster, writes the result, and refreshes the context so the newly bind influences appear in the list.

{{< collapse title="Bind Skin demonstration" collapse="true">}}
![Bind Skin demonstration](/images/documentation/ad-skin-tools/03-bind-skin.gif)
{{< /collapse >}}

## Add Influence

Use **Add Influence** when the loaded mesh already has a skinCluster and one or more new joints need to claim their natural surface regions.

1. Select the new joints in Maya and click **Add Joints To The List**.
2. In the influence list, select the pending joints you want to add.
3. Make sure those pending rows are unlocked.
4. Set Blend and Iterations.
5. Click **Add Influence**.

Only the selected pending joints are added. Existing influences remain part of the skinCluster, and the tool updates the regions claimed by the new influences. After completion, the added rows become bind influences and remain selected in the list.

{{< collapse title="Add Influence demonstration" collapse="true">}}
![Add Influence demonstration](/images/documentation/ad-skin-tools/04-add-influence.gif)
{{< /collapse >}}


## Flood

Flood recalculates the natural regions owned by selected joints that are already **bind influences**.

1. Select one or more joints that are already bind influences in the UI list.
2. In the Maya scene, select vertices, edges, or faces on the loaded mesh for a component operation. To process the whole mesh, select the loaded mesh object.
3. Set Blend and Iterations.
4. Click **Flood**.

When components are selected, only the resolved component scope is processed. You can also use Maya Soft Selection in this mode; its falloff affects the result. When the loaded mesh object is selected, the tool asks for confirmation before processing the entire mesh.

With Iterations `0`, Flood writes a hard regional result. Positive Iterations values apply smoothing to the affected region using the current Blend value. Pending joints selected alongside bind influences are ignored; use Add Influence to add those joints. Selected Flood targets must be unlocked. Values belonging to other locked influences remain protected.

{{< collapse title="Flood demonstration" collapse="true">}}
![Flood demonstration](/images/documentation/ad-skin-tools/05-flood.gif)
{{< /collapse >}}

## Smooth

Smooth relaxes the current skin weights on a component selection or across the loaded mesh.

1. In Maya, select vertices, edges, or faces on the loaded mesh. To smooth the whole mesh, select the loaded mesh object.
2. Set Blend and set Iterations to `1` or higher.
3. Click **Smooth**.

Smooth does not require a joint row to be selected. Component mode respects Maya Soft Selection falloff. Object mode displays a confirmation before processing. Locked influence values remain unchanged, and vertices with no writable weight are skipped.

{{< collapse title="Smooth demonstration" collapse="true">}}
![Smooth demonstration](/images/documentation/ad-skin-tools/06-smooth.gif)
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

With **Live Joint Selection** set to **On**, selecting a listed bind joint in the Maya scene also selects and reveals it in the UI list and refreshes the active weight visual. Set it to **Off** when you want the displayed influence to remain fixed while changing the scene selection.

The visual refreshes after relevant weight operations, Undo, and Redo. It is a temporary display session; it does not bake colour data into the skin weights.

{{< collapse title="Skin Weight Visual demonstration" collapse="true">}}
![Skin Weight Visual demonstration](/images/documentation/ad-skin-tools/07-skin-weight-visual.gif)
{{< /collapse >}}

## Mirror Skin Weights Posed Mesh

Mirror uses a persistent vertex pairing so it can work reliably on a skinned mesh in a posed state. Pairing is registered from bind reference geometry when available, so the character does not need to be returned to its bind pose just to apply mirrored weights.

### Register the mirror pairing

1. Select the mesh to mirror and click **Load Mirror Mesh**. This context is separate from the main Load Mesh context.
2. Choose the symmetry plane:
   - **YZ** mirrors across X.
   - **XZ** mirrors across Y.
   - **XY** mirrors across Z.
3. Choose the source-to-target **Direction** for that axis.
4. Set the centre plane coordinate. You can type the value directly, or select suitable centre components or the mesh transform and click **Register Selected** to calculate it from the selection.
5. Set **Tolerance**. Start with the default `0.001`; increase it only enough to resolve valid symmetrical counterparts.
6. Enter literal **Left** and **Right** joint name markers, for example `L` / `R`, `L_` / `R_`, or `_l` / `_r`. The markers may be prefixes, suffixes, or infixes, but they must be different.
7. Click **Preview Pairing**.

Preview reports legal pairs, centre vertices, unmatched vertices, ambiguous vertices, and maximum pairing error. Problem vertices are selected in Maya so they can be inspected. Preview does not overwrite an existing registered pairing.

When the preview is complete and valid, click **Register Pairing**. The geometry pairing is stored on the mesh and can be reused. If the mesh already contains pairing data, the button becomes **Replace Pairing...** and asks for confirmation before replacing it. A topology change makes an old pairing obsolete; run Preview and Replace Pairing again.

### Apply mirrored weights

1. Load a mirror mesh with an existing valid registered pairing and skinCluster.
2. Set Direction and confirm the Left/Right markers.
3. For mesh mode, leave mesh components unselected or select the complete registered region.
4. For component selection mode, select donor components from one side only. Their registered counterparts become the targets.
5. Click **Mirror Skin Weights**.

The selected direction controls which side donates weights. Joint influences are paired from the literal Left/Right markers. Locked target influence values are preserved. Do not select both sides of the same mirror region in component mode.

The Mirror **Reset** button clears the active Mirror Mesh and current UI options. It does not delete a persistent pairing already stored on the mesh.

{{< collapse title="Mirror demonstration" collapse="true">}}
![Mirror demonstration](/images/documentation/ad-skin-tools/08-mirror-optimized.gif)
{{< /collapse >}}

## Transfer Skin Weights

Transfer projects weights from one or more skinned source surfaces to one or more target meshes. Sources are the canonical donors: target influences and weights are resolved from the registered sources.

### Register sources and targets

1. Select one or more already skinned source meshes and click **Add Selected** under **Sources**. Selecting source components is allowed, but the owning mesh is registered as the donor surface.
2. Select one or more target meshes or their components and click **Add Selected** under **Targets**. Registration records the owning target meshes; the active component scope is evaluated later, when Preview Transfer runs.
3. Use **Remove Selected** or **Clear** to edit either list. A mesh cannot be registered as both a source and a target.

Right click either list to select the highlighted object or every registered object in that list within the Maya scene.

### Understand target scope

The registered Target list determines which meshes participate. The Maya component selection at the moment you click Preview overrides the scope only for matching registered targets:

| Target state at Preview | Resulting scope |
|---|---|
| No components selected on a registered target | The entire target mesh is processed |
| Components selected on a registered skinned target | Only the selected target vertices are processed |
| Components selected on an unskinned target | That component target is skipped and must be bind first |
| Unskinned target used as a whole object | A new target skinCluster can be created during Apply |

Mixed scope means that, within one operation, one target can use selected components while another registered target remains in object mode. Components from unregistered meshes do not add those meshes to the transfer.

### Preview and apply

1. Set the intended target component selection, or leave registered targets without selected components for object mode.
2. Click **Preview Transfer**.
3. Review the status summary: registered, active, and skipped targets; requested and writable vertices; locked or empty rows; and maximum source distance.
4. If the preview is valid, click **Transfer Skin Weights**.

Preview calculates and retains the exact closest source correspondence that Apply will use; Preview does not write weights. If source or target registration, the target component scope, a skinCluster, or its influence order changes after Preview, run Preview again.

During Apply:

- An unskinned target in object mode receives a new skinCluster.
- Missing source influences on an existing target are listed before they are added.
- Locked target influences are listed and skipped so their values remain unchanged.
- If either condition applies, the tool presents **Cancel** and **Proceed**. Cancel keeps the Preview available and makes no changes.
- Transfer and its adaptive boundary smoothing are applied as one operation. A failed multi target operation is rolled back rather than leaving a partial result.

The Transfer **Reset** button clears the registered Source and Target lists and the current Preview. It does not reverse a transfer that has already been applied; use Maya Undo for that.

{{< collapse title="Transfer demonstration" collapse="true">}}
![Transfer demonstration](/images/documentation/ad-skin-tools/09-transfer-optimized.gif)
{{< /collapse >}}


## Status, Undo, and diagnostics

Each operation displays a short result beneath its section and prints a more detailed report in Maya's Script Editor. Read both when a Preview is partial or when vertices are skipped because of locks, missing writable donor weight, unmatched geometry, or an invalid component scope.

Applied Bind, Add Influence, Flood, Smooth, Mirror, and Transfer operations participate in Maya's Undo workflow. If the result is not what you intended, use Maya Undo before continuing with other edits.

For support, open **Tool Help**, click **Copy Diagnostics**, and include the copied environment report with a concise description of the problem. Do not include confidential production assets or a complete licence key. Support is available at [hello@adiendendra.com](mailto:hello@adiendendra.com).
