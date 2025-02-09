# **📌 AR Cooking Book: Interactive Augmented Reality Experience**

## **🎯 Overview**

The **AR Cooking Book** is an interactive Augmented Reality (AR) experience that allows users to **place, move, rotate, and scale virtual kitchen objects** while following a step-by-step cooking guide. Using **Unity’s AR Foundation and XR Interaction Toolkit**, users can engage in a **realistic AR cooking simulation**, interacting with utensils and ingredients in their real-world space.

---

## **📖 Table of Contents**

1. **Setting Up the Project**
2. **Deploying to Android**
3. **Placing and Manipulating Objects in AR**
4. **Gesture Controls: Move, Rotate, Scale**
5. **Implementing Cooking Steps in AR**
6. **Testing and Debugging**
7. **Future Enhancements**

---

## **1️⃣ Setting Up the Project**

### **📌 A. Install Unity and Required Packages**

1. **Open Unity Hub** and create a **new 3D project**.
2. **Install AR Foundation & XR Interaction Toolkit**:
   - Go to **"Window → Package Manager"**.
   - Install:
     - ✅ **AR Foundation**
     - ✅ **XR Interaction Toolkit**
     - ✅ **ARCore XR Plugin** (Android) / **ARKit XR Plugin** (iOS)
3. Enable **XR Plugin Management**:
   - Open **"Edit → Project Settings → XR Plug-in Management"**.
   - Under **Android**, enable **ARCore**.
   - Under **iOS**, enable **ARKit**.

### **📌 B. Create AR Components in Unity**

1. **Add an AR Camera**:
   - `Hierarchy → XR → AR Session Origin`.
   - Inside **AR Session Origin**, add:
     - ✅ **AR Camera Manager**
     - ✅ **AR Raycast Manager**
     - ✅ **AR Pose Driver**
2. **Enable Plane Detection**:
   - `Hierarchy → Create Empty → Rename it "AR Plane Manager"`.
   - Add:
     - ✅ **AR Plane Manager**
     - ✅ **AR Raycast Manager**

✅ **Now, Unity is ready for AR development!** 🎉

---

## **2️⃣ Deploying to Android**

### **📌 A. Enable Developer Mode on Android**

1. Open **Settings → About Phone → Tap "Build Number" 7 times**.
2. Enable **USB Debugging** in **Developer Options**.
3. Connect your phone to your PC via **USB**.

### **📌 B. Set Up Unity for Android Deployment**

1. In Unity, **go to "File → Build Settings"**.
2. Select **Android** and click **Switch Platform**.
3. Install **Android Build Support & SDK** via Unity Hub.
4. Set **Player Settings**:
   - **Minimum API Level:** Android 7.0 or higher.
   - **Scripting Backend:** IL2CPP.
5. Click **Build & Run** to install the app on your Android device.

✅ **Now, your AR Cooking Book runs on Android!** 📱🚀

---

## **3️⃣ Placing and Manipulating Objects in AR**

### **📌 A. Implement AR Object Placement**

1. **Create an "AR Placement Manager"** GameObject.
2. **Attach the following script** to enable object placement:

```csharp
using UnityEngine;
using UnityEngine.XR.ARFoundation;
using UnityEngine.XR.ARSubsystems;
using System.Collections.Generic;

public class ARPlacement : MonoBehaviour
{
    public GameObject objectToPlace;
    public ARRaycastManager raycastManager;
    private List<ARRaycastHit> hits = new List<ARRaycastHit>();

    void Update()
    {
        if (Input.touchCount > 0 && Input.GetTouch(0).phase == TouchPhase.Began)
        {
            Touch touch = Input.GetTouch(0);
            if (raycastManager.Raycast(touch.position, hits, TrackableType.PlaneWithinPolygon))
            {
                Pose hitPose = hits[0].pose;
                Instantiate(objectToPlace, hitPose.position, hitPose.rotation);
            }
        }
    }
}
```

3. Assign a **prefab (e.g., pot, knife, or ingredient)** to `objectToPlace`.

✅ **Now, users can tap on surfaces to place kitchen items!** 🎯

---

## **4️⃣ Gesture Controls: Move, Rotate, Scale Objects**

### **📌 A. Enable Object Interaction**

1. Open your **cooking object prefab** (e.g., pot).
2. Add:
   - ✅ **XR Grab Interactable**
   - ✅ **Rigidbody** (`Use Gravity = False`)
   - ✅ **Collider**

### **📌 B. Implement Pinch-to-Scale (Resize Objects)**

1. **Attach this script** to all interactable objects:

```csharp
using UnityEngine;

public class PinchToScale : MonoBehaviour
{
    private float initialDistance;
    private Vector3 initialScale;

    void Update()
    {
        if (Input.touchCount == 2)
        {
            Touch touch0 = Input.GetTouch(0);
            Touch touch1 = Input.GetTouch(1);

            if (touch0.phase == TouchPhase.Moved || touch1.phase == TouchPhase.Moved)
            {
                float currentDistance = Vector2.Distance(touch0.position, touch1.position);
                if (initialDistance == 0)
                {
                    initialDistance = currentDistance;
                    initialScale = transform.localScale;
                }
                else
                {
                    float factor = currentDistance / initialDistance;
                    transform.localScale = initialScale * factor;
                }
            }
        }
        else
        {
            initialDistance = 0;
        }
    }
}
```

✅ **Now, users can move, rotate, and resize objects in AR!** 🎮🔥

---

## **5️⃣ Implementing Cooking Steps in AR**

1. Display **step-by-step instructions** in a UI overlay.
2. Implement **voice commands** (e.g., "Next Step") to move through the recipe.
3. Add animations for **ingredient mixing and food preparation**.

---

## **6️⃣ Testing and Debugging**

- Run the app on multiple Android/iOS devices.
- Optimize performance by reducing **object complexity**.
- Check for **gesture accuracy and interaction issues**.

---

## **7️⃣ Future Enhancements**

🔹 **Multiplayer Cooking Mode** (Shared AR experience).\n🔹 **Real-time Ingredient Recognition**.\n🔹 **Integration with Smart Kitchen Appliances**.

🚀 **Now, your AR Cooking Book is fully functional!** 🎉 Let me know if you need further improvements! 😊🔥

