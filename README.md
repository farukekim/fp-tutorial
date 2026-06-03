[Türkçe Anlatım İçin Buraya Tıklayın](READMETR.md)

# Filament Painting Usage Tutorial

This tutorial explains the Filament Painting app from the first launch through STL export. The app is designed to turn photos into layered 3D filament art, plan filament transitions, preview the 3D mesh, save projects, and export STL files.

## 1. Getting to Know the App

On the main screen, the workspace consists of several panels:

- **Mesh Preview**: Shows the generated 3D model live. From here, you can select the mesh mode, import a source project, save the project, and export STL.
- **Image Preview**: The area for loading a photo, inspecting the image, selecting layers from the image, and sampling colors for Color Match.
- **Palette Engine**: Manages the filament color order and layer ranges to be used in the print.
- **Geometry Engine**: In Color Match mode, manages the geometry and active/inactive layers according to color matching.
- **Filament Library**: The library containing built-in and custom filaments. You can mark filaments, filter them, and drag them onto the core panels.
- **Project Controls**: Contains the model height, layer height, base layer height, base thickness, width, and height settings.

On wide screens, the panels appear side by side. On smaller screens, some panels can be opened and closed with **Show / Hide** buttons.

## 2. Loading the First Photo

1. Go to the **Image Preview** panel.
2. Tap the **Load Image** button.
3. Select an image from the photo picker.
4. After the image is loaded, you can switch to another image later with the **Change Image** button.

The app accepts JPG, PNG, WEBP, and SVG sources according to the image flow supported in the user interface. When an image is loaded, the app automatically scales the **Width** and **Height** values while preserving the longest edge of the model according to the current measurement.

For good results, choose images with high contrast, clear silhouettes, and minimal blur. Transparent areas may behave like empty areas during STL mesh generation.

![Load Image](<loadimage.gif>)

## 3. Adjusting Model Dimensions

The **Project Controls** panel contains the basic fields that define the print geometry:

- **Mesh Height**: The total target thickness of the model. The default value is `2.24 mm`.
- **Layer Height**: The layer height you will use in the slicer. The default value is `0.08 mm`.
- **Base Layer Height**: The height of the first base layer. The default value is `0.16 mm`.
- **Base Thickness**: The minimum base thickness of the STL geometry. The default value is `0.48 mm`.
- **Width**: The model width. The default value is `200 mm`.
- **Height**: The model height. The default value is `200 mm`.

Layer count calculation:

Example: With a `2.24 mm` mesh height, a `0.16 mm` base layer, and a `0.08 mm` layer height, the result is a project of approximately 27 layers.

Only numbers and decimal points can be entered in numeric fields. If a field is left empty, the app restores the default value.
![3D Mesh Model Sizes](<3dmeshmodelsizes.gif>)

## 4. Inspecting the 3D Model with Mesh Preview

When a photo is loaded, the **Mesh Preview** panel generates the 3D preview.

Preview controls:

- **Drag to rotate**: Rotate the model with one finger or with the mouse.
- **Two fingers to pan**: Pan the model with two fingers.
- **Pinch to zoom**: Zoom in and out.
- **Reset**: Resets the camera view.
- Fullscreen icon: Displays the mesh preview larger.

The preview may pause GPU work while the app is inactive. When you return to the app, the preview is prepared again.
![Mesh Preview](<meshpreview.gif>)

## 5. Selecting Mesh Mode

There are two modes in **Mesh Preview > Mesh Mode**:

### Standard Mesh

Standard Mesh is free. It generates a layered height model from the image's brightness/luminance information. You manage your own filament palette through the **Palette Engine**.
Luminance directly controls layer stacking. Darker regions remain thin at the base, whereas lighter areas gain thickness, reaching the highest Z-axis points.

This mode is suitable for:

- Simple projects 
- Personal projects that do not require a subscription.

### Color Match

Color Match requires a monthly subscription. It analyzes the colors in the image, matches them with colors in the filament library, and helps automatically prepare palette and geometry core assignments.

With Color Match:

- You can perform automatic dominant color analysis. Dominant Color is a experimental feature. It may not work with some images. To get better results, assign filaments manually. 
- You can optimize the filament sequence according to the image.
- You can disable some layers through the Geometry Engine.
- You can select the color matching method.
- You gain access to a commercial use license while the subscription is active.

If the subscription is not active when Color Match is selected, the subscription screen opens.

## Note:
Dominant Colors is an experimental feature. While this feature yields great results for certain images, it may not be perfect for every case. Keep in mind that the Dominant Colors algorithm operates independently and does not directly influence Color Match algorithms. To achieve the absolute best results, take full control by manually fine-tuning your color assignments in both the Geometry and Palette engines."

![Mesh Modes](<meshmodes.gif>)

## 6. Color Match Subscription and Restore

The Color Match screen includes the following options:

- **Subscribe for ... / month**: Starts the monthly subscription through Apple.
- **Restore Purchases**: Restores a subscription previously purchased with the same Apple ID.
- **License Terms**: Shows the commercial use terms.
- **Privacy**: Shows privacy information.
- **Tutorials**: Opens the tutorial link.
- **Apple EULA**: Opens Apple's standard EULA page.

Standard Mesh remains free for personal projects. According to the app's license text, an active monthly subscription is required for 3D prints or digital files intended for sale.

## 7. Color Match Automatic Pipeline

When Color Match is active, the **Dominant Colors** control works in the **Mesh Preview** panel.

1. Enable **Color Match** mode.
2. Select the **Dominant Colors** value. The range is from `2` to `8`, with a default of `6`.
3. Tap the play button.
4. During the process, a progress bar and status messages appear.
5. When the pipeline is complete, the Palette Engine and Geometry Engine are updated automatically.

The pipeline analyzes the image, extracts meaningful target colors for printing, selects suitable filaments, creates layer ranges, and may disable some geometry layers.

![Dominant Colors Experimental](<dominantcolors.gif>)

## 8. Color Match Modes

When Color Match is active, the matching method is selected in the **Modes** section:

- **0 RGB**: More direct color matching based on RGB distance.
- **2 Lab+**: Lab-based, improved perceptual matching.
- **3 Lab**: Perceptual matching based on the Lab color space.

The best mode may vary depending on the image and filament set. For highly saturated images or photos containing skin tones/intermediate tones, switch between modes and compare the preview result.

![Color Match Preview](<colormatchpreview.gif>)
![Color Match Manual for Better Match](<colormatchmanual.gif>)

## 9. Brightness Settings

Inside the fullscreen mesh preview, there is a **Brightness Settings** button.

Settings:

- **Target > Edit Image**: When enabled, the brightness adjustment is applied to the input image. When disabled, it is applied on the mesh preview side.
- **Method**: Selects the brightness curve method. Examples: Standard, Clean Lift, Soft Lift, Filmic Balance, Shadow Recovery, Highlight Guard, Soft Contrast.
- **Power**: Adjusts the strength of the curve. Range: `1.00` to `10.00`.
- **Alternate Edit**: Enables or disables the alternative editing path.
- **Bright Adjust**: General brightness adjustment. Range: `-1.00` to `1.00`.
- **Reset Settings**: Restores all brightness settings to their defaults.

If the image is too dark, try Shadow Recovery or Clean Lift. If bright areas are blown out, Highlight Guard or Soft Contrast may give a more balanced result.

![Brightness Settings](<brightnessSettings.gif>)

![Edit Image Brightness Settings](<editimageBS.gif>)


## 10. Using the Filament Library

The **Filament Library** panel manages the app's filament database.

### Filtering filaments

- You can select types such as PLA, PETG, ABS, and TPU from the material tabs at the top.
- You can type a brand or filament name in the **Filter** field.
- You can filter multiple filament types at the same time with **Type Filters**.
- Filaments are separated as **Owned** and **Unowned**.

### Marking as Owned

When you tap a filament row, that filament changes between owned and unowned. This information is stored locally on the device.

### Adding a filament

1. Tap the **Add Filament** button.
2. Enter the brand name in the **Brand** field.
3. Enter the filament name in the **Name** field.
4. Select **Material / Type** or enter a custom type in the **Custom Type** field.
5. Enter the color in `#RRGGBB` format in the **Color Hex** field.
6. Enter the **Transmissivity** value.
7. Optionally enable **Mark as Owned**.
8. Save with **Save**.

A second filament with the same brand, name, type, color, and transmissivity combination cannot be added.

### Deleting a filament

Select **Delete Filament** from the three-dot menu on the row.

- Custom filaments are permanently deleted from the device.
- Bundled filaments that come with the app are not removed from the app package; they are only hidden on this device.

![Add Filament](<addfilament.gif>)
![Delete Filament](<deletefilament.gif>)

## 11. Setting Up Filament Order with Palette Engine

The **Palette Engine** shows the filament colors to be used in the print and the layer ranges in which they will be active.

Basic concepts:

- The vertical color bar shows the layers.
- The small handles on the right are slicer boundaries.
- The numbers on the left show the boundary layers.
- Each color block is a filament segment.

Usage:

1. Drag a filament row from the Filament Library.
2. If you drop it onto a single layer in the Palette Engine, only that layer changes.
3. If you drop it near a slicer line, it is applied to the entire related layer range.
4. Drag the handles up/down to change the filament transition layers.
5. Dragging the first handle to the very bottom removes the first filament segment and brings the next segment forward.

The Palette Engine calculates the layer-by-layer blended appearance using the transmissivity and color values of the filaments.

### Undo, Redo, and transfer

Above the Palette Engine:

- Back arrow: Reverts the last change.
- Forward arrow: Reapplies the reverted change.
- Right arrow: Copies Palette Engine assignments to the Geometry Engine side.

Undo/redo history is kept per panel.

## 12. Using the Geometry Engine

The **Geometry Engine** becomes active in Color Match mode. If there is no subscription or Color Match is disabled, the panel appears locked.

The Geometry Engine manages which layers of the mesh geometry will be used according to the color match in the image.

Usage:

- You can drag and drop filaments in the same way as with the Palette Engine.
- You can change geometry slicer boundaries with the handles.
- A single tap on a layer toggles that layer active/inactive.
- Disabled layers show **OFF** or an X mark.
- A double tap on a layer highlights that layer in the preview.

The left arrow at the top copies Geometry Engine assignments to the Palette Engine side. Disabled layer information on the Geometry side is not copied to the Palette Engine.

## 13. Finding a Layer from the Image

In the **Image Preview** panel, you can find the related mesh layer by tapping or pressing and holding on the image.

- Short tap: Highlights the layer corresponding to the tapped point in the preview and core panels.
- Dragging or a long-press-like gesture: Opens the magnifier, samples the color, and lists the closest filaments.

This feature is useful for seeing which layer a detail corresponds to and for fine-tuning filament transitions.

![Hightlight Layer](<hightlightLayer.gif>)

## 14. Color Sampling from the Image and Manual Color Match

When Color Match is active, you can select colors on the Image Preview.

1. Press and hold or slightly drag over the desired color on the image.
2. The magnifier and selected color indicator open.
3. In the **Find Closest Filament** popup, the sampled HEX color and the closest filaments are listed.
4. Add this color to the manual dominant color list with **Add**.
5. After selecting at least 2 colors, tap the **Process** button.

Selected colors appear as small horizontal color tags. You can remove a color from the list by tapping its tag. The maximum number of manual colors is `8`.

![Pick Colors and Use Auto Color Match](<dominantcolorspickcolors.gif>)

## 15. Describe Screen

Tap the **Describe** button from **Project Controls** or from the bottom control bar.

The Describe screen summarizes:

- Print summary: infill, layer height, and base layer information.
- **Project**: Model size, base thickness, and actual total thickness.
- **Filaments**: Unique filaments used, material, HEX, and transmission information.
- **Swap Instructions**: Which filament to switch to at which layer.

You can use this screen as a pre-print checklist. When entering filament changes in the slicer, pay particular attention to the **Layer #** and height values.

## 16. Exporting STL

1. A photo or project source must be loaded.
2. The mesh preview must be generated successfully.
3. Open the **Mesh Preview > Actions** section.
4. Tap the **Export STL** button.
5. Select the file location and save it.

The STL is generated in binary format. When possible, the export name is created from the source image or project name; otherwise, a default name such as `selected_image_preview.stl` is used.

During STL export, if the image is too small, completely transparent, or mesh index data cannot be generated, the app shows an error message.

![Saving Project, Exporting Stl and Loading Project](<saveprojectexportstl.gif>)


## 17. Saving a Project

1. Load an image and adjust your settings.
2. Open the **Mesh Preview > Actions** section.
3. Tap the **Save Project** button.
4. Save the `.fpproj` file to the location you want.

The saved project includes:

- Image data.
- Mesh mode.
- Mesh height, layer height, base layer, base thickness, width, and height.
- Palette Engine slicer and filament segments.
- Geometry Engine slicer and filament segments.
- Disabled Geometry Engine layers.
- Color Match match method.
- Brightness settings.

`.fpproj` files are encrypted with a key stored in the device keychain. Therefore, secure project files are designed to be opened by the app installation that created them.

![Saving Project, Exporting Stl and Loading Project](<saveprojectexportstl.gif>)

## 18. Importing a Project

There are two sources in **Mesh Preview > Source**:

- **Use Image**: Uses the currently loaded image.
- **Project**: Imports a project file.

When Project is selected, the file picker opens. The app can read `.fpproj` and compatible JSON project files.

If the imported file is a Filament Painting project, the app applies its settings and image to the main workspace. If a compatible preview project format contains an image or STL reference, it can be used as the preview source.

### Use Project STL

When the Project source is selected and the project contains an STL reference, the **Use Project STL** toggle appears. When this option is enabled, the preview tries to use the STL path inside the project.

![Saving Project, Exporting Stl and Loading Project](<saveprojectexportstl.gif>)

## 19. Privacy and Local Processing

In the app flow, selected images, project files, custom filament records, and STL export operations are processed locally on the device.

In the current codebase:

- There is no account login.
- There are no ads.
- There is no third-party analytics.
- There is no cross-app tracking.
- Photos, STL files, project files, or custom filaments are not uploaded to the developer's server.
- Purchase and restore operations run through Apple StoreKit.

The **Privacy** button also shows this information inside the app.

## 20. License Terms

The **License Terms** screen summarizes the commercial use terms:

- You can create personal projects with Standard Mode without an active subscription.
- While an active monthly subscription is in place, you have the right to sell 3D prints and digital files created with the app.
- If the subscription ends or is canceled, the commercial sales right is paused until the subscription becomes active again.
- It is the user's responsibility to obtain the necessary rights for intellectual property, logos, characters, brands, or images belonging to others.

## 21. Recommended End-to-End Workflow

1. Load an image with **Load Image**.
2. Check the Width, Height, Mesh Height, Layer Height, and Base settings in **Project Controls**.
3. Stay in **Standard Mesh** mode for the free workflow.
4. If you want more automatic color matching, enable **Color Match** mode and activate the subscription.
5. Mark the filaments you own as **Owned** in the Filament Library.
6. If necessary, add your own filaments with **Add Filament**.
7. Drag and drop filaments into the Palette Engine.
8. Adjust the filament transition layers by moving the slicer handles.
9. If you are using Color Match, select the number of Dominant Colors and run the automatic pipeline.
10. In the Geometry Engine, disable unnecessary layers or edit the geometry filament sequence.
11. Tap details on the Image Preview to highlight the related layers.
12. Rotate and zoom the model in Mesh Preview to inspect it.
13. If needed, balance dark/bright areas with **Brightness Settings**.
14. Check the filament and swap instructions from the **Describe** screen.
15. Save the `.fpproj` with **Save Project**.
16. Export the print-ready STL file with **Export STL**.
17. Import the STL file into the slicer, and slice it with 100% infill and the layer height values from the app.
18. Set filament changes according to the swap instructions on the Describe screen.

## 22. Practical Notes for Printing

- The app recommends 100% infill on the Describe screen.
- Enter the layer height value in the slicer exactly the same as the value in the app.
- Base layer and base thickness values affect the durability of the model.
- Increasing the Width/Height value may give better results for very fine details.
- Too many filament segments increase print time and the number of swaps.
- Since the transmissivity value affects color blending, enter a realistic value when adding custom filaments.
- If the Color Match result does not look perfect, compare by trying different Dominant Colors counts, match methods, and brightness settings.

## 23. Common Situations

### Mesh preview is not visible

- First make sure you have loaded an image.
- Check that Mesh Height, Layer Height, Width, and Height values are not zero.
- If the app has just returned from the background, wait briefly for the preview to regenerate.

### Export STL is disabled

STL export becomes active only after the mesh payload has been generated. First wait for the preview to be generated successfully.

### Save Project is disabled

An image must be loaded before a project can be saved.

### Color Match is locked

Color Match requires a monthly subscription. If you have a subscription, use **Restore Purchases**.

### Project file does not open

Secure `.fpproj` files depend on the keychain key of the installation that created them. If they do not open on another device or installation, use the image loading flow or the compatible project import format.

### Filament looks wrong

Check the color HEX and Transmissivity values in the filament library. If a custom filament was entered incorrectly, delete it and add it again with the correct values.

## 24. Panel Shortcuts

- **Hide / Show Filament Library**: Collapses or restores the filament panel on wide screens.
- **Core Panels Show / Hide**: Opens/closes the Palette Engine and Geometry Engine area on compact screens.
- **Project Controls Show / Hide**: Opens/closes the dimension fields on compact screens.
- **Done**: Closes the input while the keyboard is open.
- **Reset**: Resets the mesh camera.
- **Fullscreen**: Opens the mesh preview in fullscreen.

## 25. Short Terms

- **Layer**: A layer in the print.
- **Slicer boundary**: The layer boundary where the filament change occurs.
- **Palette Engine**: The color/filament blending plan.
- **Geometry Engine**: The geometry layer plan for Color Match.
- **Transmissivity / TD**: A value that affects the filament's light transmission or color blending behavior.
- **Dominant Colors**: The number of main target colors extracted from the image.
- **Match Method**: Color Match's color matching algorithm.
- **Base Thickness**: The minimum base thickness of the model.
- **Mesh Height**: The total target thickness of the model.
- **STL**: The 3D model file to be transferred to the slicer.
- **FPPROJ / .fpproj**: The Filament Painting project file.

## Showcase

### Videos

[Standart Mode Preview](https://www.youtube.com/watch?v=deloUQGVre4)
[Color Match Mode Preview](https://www.youtube.com/watch?v=9kdz2RvdSu0)

1. [Bookmark 1 Color Match](https://www.youtube.com/watch?v=x3OFoDtGYiQ)
2. [Bookmark 2 Color Match](https://www.youtube.com/watch?v=zj7FIFvfqYU)
3. [Bookmark 3 Color Match](https://www.youtube.com/watch?v=sfgcbiDYI00)

### Images

![Bookmark 1 Color Match](<bookmark1.jpeg>)
![Bookmark 2 Color Match](<bookmark2.jpeg>)
![Bookmark 3 Color Match](<bookmark3.jpeg>)
