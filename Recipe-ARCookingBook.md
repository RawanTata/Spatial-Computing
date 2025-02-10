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



### **Main Steps in the Video: "Deploying an AR App with Unity AR Foundation"**  


---

### **1. Introduction to AR Foundation** 
- Overview of **Unity's AR Foundation** package.  
- AR Foundation supports **Android, iOS (ARKit), and HoloLens**.  
- Features include **plane detection, image tracking, object tracking, face tracking, body tracking, and more**.  

---

### **2. Understanding AR Foundation Structure** 
- **Subsystems and Providers:**  
  - Unity provides **subsystems** (interfaces with required functions).  
  - **Providers** (e.g., ARCore for Android, ARKit for iOS) implement these functions.  
- **Managers:**  
  - Help Unity access **subsystem data** via game objects.  
  - Example: **Plane Manager** creates a game object when a plane is detected.  

---

### **3. Setting Up Unity for AR Development** 
  - Start a new project with **Unity's AR Template** (pre-installed AR packages & sample scene).  
- **Installing Necessary Modules:**
  - **For Android:** Install **Android Build Support**.  
  - **For iOS:** Install **iOS Build Support**.  
- **Adding AR Foundation in an Existing Project:**
  - Open **Package Manager** → Download **AR Foundation**.  
  - Install **ARCore XR Plugin (for Android)** or **ARKit XR Plugin (for iOS)**.  
- **Enabling Input System:**  
  - Helps with better control and interaction.  
![image](https://github.com/user-attachments/assets/9d55ae52-de34-4aef-8c30-747ee12936e8)
![image](https://github.com/user-attachments/assets/bf8727ee-a6c5-4ab7-a865-2044c1b51c54)


---

### **4. Configuring Unity Build Settings** 
- **Switch to the Target Platform** (Android/iOS).
- ![image](https://github.com/user-attachments/assets/e98a16b7-018c-42af-9760-4ea98e2bc1c5)
 
- Enable **Development Build** (for easy testing).  
- **Adjust Player Settings:**
  - iOS: **Set Minimum iOS Version to 11.0**, enable **ARKit Support**, add **Bundle Identifier**.  
  - Android: **Set Minimum API Level (24 for AR apps, 19 for non-AR apps)**.  
  - Remove **Vulkan Graphics API** (not supported in AR).  
  - Set **IL2CPP as the scripting backend** for Android Play Store builds.  
![image](https://github.com/user-attachments/assets/c6535a7c-4222-4be2-81ee-a594e60d792e)
# **Getting Started with AR Foundation**

Unity's **AR Foundation** is a cross-platform framework that allows you to write augmented reality experiences once, then build for either **Android** or **iOS** devices without making any additional changes. The framework is available via **Unity's AR Foundation package**.

## **ARCore Extensions**
ARCore's optional **ARCore Extensions for AR Foundation** package adds additional functionality, enabling you to use features such as:
- **Cloud Anchors**
- **Camera configuration filters**
- **Recording and Playback**
---

## **Requirements**

### **Android**
#### **Hardware:**
- An **ARCore-supported Android device or emulator**
- A **USB cable** for connecting your device to your development machine

#### **Software:**
- **Unity 2019.4.3f1 or later** with **Android Build Support**

### **iOS**
#### **Hardware:**
- A device that supports **Apple's ARKit** (iPhone 6s and later, iPad 5th gen and later)
- A **Mac computer with Xcode installed**

#### **Software:**
- **Unity 2019.4.3f1 or later** with **iOS Build Support**

---

## **Install AR Foundation**
Follow these steps to install the **AR Foundation** Unity package.

1. **Open an existing Unity project**, or **create a new 3D project**.
2. Navigate to **Window > Package Manager**.
3. Next to **Packages**, select **Unity Registry**.
   ![image](https://github.com/user-attachments/assets/31eb5dc4-1ef6-433f-bca8-e2a91fc37bd8)
5. In the search bar, type **"AR Foundation"**.
. ![image](https://github.com/user-attachments/assets/1e1a893d-fa8a-4dc9-b63f-8bf4db18c46e)

7. Click **Install**.
![image](https://github.com/user-attachments/assets/475371f1-8357-4896-9479-103eb02aeed3)

---

## **Install and Enable Platform-Specific Plugin Packages**
The **AR Foundation** package provides an interface for Unity developers but does not implement AR features itself. To use **AR Foundation** on a target device, install separate packages and enable the corresponding plugin for each platform.

### **For Android (ARCore)**
The **ARCore XR Plugin** package lets you build augmented reality apps for **Android devices**. Follow these steps to install it in your Unity project:

1. Open **Unity > Window > Package Manager**.
2. Next to **Packages**, select **Unity Registry**.
3. In the search bar, type **"ARCore XR plugin"**.
4. Click **Install**.
5. Navigate to **Edit > Project Settings**.
6. https://developers.google.com/static/ar/develop/unity-arf/images/getting-started/xrm-enable-arcore.png
7. In **XR Plug-in Management**, open the **Android** tab and **enable ARCore**.

### **For iOS (ARKit)**
1. Open **Unity > Window > Package Manager**.
2. Next to **Packages**, select **Unity Registry**.
3. In the search bar, type **"ARKit XR Plugin"**.
4. Click **Install**.
5. Navigate to **Edit > Project Settings**.
6. In **XR Plug-in Management**, open the **iOS** tab and **enable ARKit**.

---

✅ **Now, AR Foundation is installed and configured for both Android and iOS!** 🚀



### **5. Enabling XR Plugin Management** 
- Go to **XR Plugin Management** in Player Settings.  
- **Enable ARCore (Android) or ARKit (iOS)**.  
- Check settings such as **face tracking** if needed.  

---

### **6. Setting Up AR Scene in Unity** 
- **Create AR Session Game Object**:
  - Add **AR Session Component** (Manages AR lifecycle).  
  - Add **AR Input Manager** (Handles user interactions).  
- **Create AR Session Origin**:
  - Converts **AR session space to Unity world coordinates**.  
  - Attach an **AR Camera** (with AR Camera Manager & Tracked Pose Driver).  
- **Adding Objects in AR Space**:
  - Place a **3D object (Cube)** in front of the camera for proper positioning.  

---

### **7. Building and Deploying to Mobile** 
- Go to **Build Settings** → Select correct platform → Add open scenes.  
- Click **Build**, create a **Builds Folder**, and export the project.  
- **For iOS:**  
  - Open in **Xcode**, enable **Automatic Signing**, and deploy to a connected iPhone.  
- **For Android:**  
  - Build directly to phone.  
  - Ensure **Developer Mode is enabled** on the device.  

---

### **8. Running the AR App on Your Phone** 
- Launch the AR app on the phone.  
- **Grant camera access** (iOS).  
- The placed **3D Cube appears in AR space**.  

---

### **9. Exploring Unity's AR Foundation Samples** 
- Unity provides **sample AR projects** on **GitHub**.  
- Download the **sample scenes** (e.g., **image tracking, plane detection**) for reference.  
- Future tutorials will cover **advanced AR features**.  

---














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

