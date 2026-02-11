

## **Step 1: Define the Purpose of Your Boilerplate**

Before creating the boilerplate, decide what it should include. Common elements in a TouchDesigner boilerplate:

* **UI Components** (buttons, sliders, parameters)
* **Rendering Pipeline** (Camera, Light, Geometry)
* **Base Network Organization** (folders, color coding)
* **Custom Scripts & Python Callbacks**
* **Performance Optimizations**

---

## **Step 2: Open TouchDesigner and Set Up the Project**

1. Launch **TouchDesigner**.
2. Go to **Edit → Preferences** and configure settings like FPS (frames per second) and default file save location.
3. Save the project immediately with **File → Save As**, naming it something like **boilerplate.toe**.

---

## **Step 3: Organize Your Network Layout**

1. **Create a Root Organization** in `/project1`:

   * Right-click and **Create Base COMP** → Name it **"Main"**
   * Inside "Main", create subfolders:

     * **"Rendering"** (for cameras, lights, and 3D objects)
     * **"UI"** (for user interface elements like sliders & buttons)
     * **"Logic"** (for Python scripts & triggers)
     * **"Effects"** (for shaders, feedback loops, and post-processing)

2. **Use Color Coding & Labels**:

   * Right-click nodes → Set a color for each category (e.g., UI elements = blue, rendering = green).
   * Use the **Text DAT** to document what each section does.

---

## **Step 4: Set Up a Basic Rendering Pipeline**

1. **Inside "Rendering" Base COMP**, create:

   * A **Geometry COMP** (name it `geo1`)
   * A **Camera COMP** (`cam1`)
   * A **Light COMP** (`light1`)
   * A **Render TOP** (`render1`) → Connect **cam1 & geo1**
   * A **Constant MAT** (to give geo1 a basic material)

2. Test it by plugging `render1` into a **Null TOP** and previewing the output.

---

## **Step 5: Add a UI System (Sliders & Buttons)**

1. **Inside "UI" Base COMP**, create:

   * A **Container COMP** (`container1`) → This will hold the UI elements
   * Inside `container1`, add:

     * A **Slider COMP** (name it `slider1`)
     * A **Button COMP** (`button1`)

2. **Connect the UI to Logic:**

   * Drag `slider1` onto a **Text DAT** to generate a Python reference.
   * Modify the slider’s `Value` field to control an aspect of the scene (e.g., light intensity):

     ```python
     op('light1').par.intensity = op('slider1').par.value0
     ```

---

## **Step 6: Implement Custom Python Scripts**

1. **Inside "Logic" Base COMP**, create a **Text DAT** (`script1`)

2. Write a simple script to toggle an effect when a button is pressed:

   ```python
   def onClick():
       effect = op('Effects/blur1')
       effect.par.bypass = not effect.par.bypass
   ```

3. Link `onClick()` to `button1` by dragging `script1` onto the Button COMP and selecting **"Run on Click"**.

---

## **Step 7: Optimize Performance**

* Use **Null TOPs** to prevent unnecessary recalculations.
* Set **Viewer Flag OFF** for non-essential nodes.
* Adjust **TOP & CHOP resolutions** to be as low as needed.
* Enable **TouchDesigner Perform Mode** (`F1`) to check real-time performance.

---

## **Step 8: Save as a Boilerplate Template**

1. Save the file as **boilerplate.toe**.
2. Optionally, save UI components as `.tox` (TouchDesigner component files) for reuse.
3. Set up **Auto-Save** (`Edit → Preferences → Auto Save`).

---

### **Next Steps: Expanding Your Boilerplate**

* Add a **Shader Pipeline** with GLSL TOPs.
* Include **MIDI or OSC Input** for external control.
* Create a **Custom UI Dashboard** for better controls.
* Optimize with **GPU-based processing**.

Would you like an example `.toe` file with a basic boilerplate setup? 🚀
