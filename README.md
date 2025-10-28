# Touchpad Visualization Debugging Tool

The Touchpad Visualizer Window is a developer option introduced in the Android Operating System to provide real-time visualization for debugging touchpad interactions. Enabled via developer settings, it helps developers test and refine touchpad functionality on Android devices with interactive, on-screen feedback.

This feature was developed by me and another intern on the Android Input Framework team at Google’s London office during summer 2024. It is now integrated into the Android codebase, used by billions worldwide.

## Features
- **Gesture Visualization**: Displays the type of gesture detected, such as swipe, zoom, or move.
- **Pressure and Click Detection**: Displays touch pressure and click events for precise debugging.
- **Multi-Touchpad Support**: Allows seamless switching between multiple connected touchpads.
- **Finger Movement Tracing**: Visualizes finger movements by drawing traces on the screen.
- **Drag and Positioning**: Enables users to drag the debug window to any part of the screen, ensuring it stays within bounds.

## Commit History
Below is the list of public commits made to the Android OS source code for this feature. Each entry includes a description of the changes and a link to the specific commit.

### Commit 1
**Description**: Create prototype for TouchpadDebugView. The `TouchpadDebugViewController` manages the lifecycle of the `TouchpadDebugView`, which provides visual debugging information for touchpad devices. This controller listens for touchpad device additions and removals and appropriately shows or hides the debug view in response.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/ea5a5df8f5e42ab13b3c6cb7991e45f94e5a5567)

### Commit 2
**Description**: Create `getTouchpadHardwareProperties()` and link it to native code. Added a new method `getHardwareProperties` that returns an instance of a new class, `HardwareProperties`, in Java. This method is also linked to its native implementation.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/e98ecc5888975d65114071a9c0cd9136d5e9768f)

### Commit 3
**Description**: Merge "Create getTouchpadHardwareProperties() and link it to native code" into main.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/f85cdacaf226f884d70985512fa16d47fc449810)

### Commit 4
**Description**: Implement draggability feature for `TouchpadDebugView`. Added a draggability feature, allowing users to reposition the view by touch. Constrained the view's movement to stay within the screen boundaries, preventing it from being dragged off-screen. Handled screen rotation events by adjusting the view's position to remain within the new screen dimensions after rotation.

**Test Description**: Added unit tests to cover scenarios such as dragging the view, ensuring the view stays within screen bounds, verifying no movement for minimal touch input, and confirming the view returns to its original position when the action is canceled. Manual testing was also performed to validate these behaviors.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/5b20222bb90fd9730b3b488595628b9561fe1b1e)

### Commit 5
**Description**: Change `TouchpadDebugView` color on touchpad button clicked. Sent `HardwareState` of the touchpad to the `TouchpadDebugView` and changed the color of the view each time the touchpad button is clicked.

**Test Description**: Manual testing by checking that the `TouchpadDebugView` changes color each time the touchpad button is pressed and unit testing to verify the color change by comparing the old color of the view with the new one.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/3ed2996cf30c37172521eeafa26ed54c89ef72f5)

### Commit 6
**Description**: Added new custom `View` to `TouchpadDebugView`. Added a custom view that contains the representation of the fingers. Fetched the touchpad name inside the `TouchpadDebugView`.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/ce15a76c64813796f128f85fa1360eab025175b3)

### Commit 7
**Description**: Handle multiple touchpads in `TouchpadDebugViewController`. Added logic to handle multiple touchpad connections/disconnections, avoiding a state where a touchpad is connected but no view is displayed after the original touchpad is disconnected. Ensured the view's color changes only when a `HardwareProperty` of the same ID is received.

**Test Description**: Updated unit tests to test sending `HardwareProperties` with different `deviceIds` to the view and verify that only the one with the same `deviceId` affected the view. Manual testing by connecting multiple touchpads and verifying the result of disconnecting the first or second touchpad to ensure desired behavior.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/4addccb46f5aa6710da305c86eb1f0ed0fd73cb4)

### Commit 8
**Description**: Display the gesture name on the `TouchpadDebugView`. Fetched the gesture type and displayed it on the `TouchpadDebugView`, updating the view each time a new gesture is received. Rounded the view edges for better aesthetics.

**Test Description**: Added unit tests to send a gesture type index to the `TouchpadDebugView` and confirm the displayed gesture name matches the sent one.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/3d1dc8b0c919fc2c6e482082b4485c6d7c6acbe7)

### Commit 9
**Description**: Merge "Display the gesture name on the TouchpadDebugView" into main.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/db45101ca742bee581dbfba02b410968e8eaac41)

### Commit 10
**Description**: Add touchpad selection dropdown menu. Added a dropdown menu next to the touchpad name that displays a list of all connected touchpads. This menu allows users to switch between available touchpads by selecting from the list.

**Test Description**: Manual testing by verifying that the touchpad switch logic works as intended and that the dropdown menu is updated whenever a touchpad is added/removed.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/3c9b6a96707d25542e038df6e7fd09c45aafa5ba)

### Commit 11
**Description**: Disabled two-finger dragging on `TouchpadDebugView`.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/841b68bbf14452c46cf82a066a51bdd5545af2a0)

### Commit 12
**Description**: Fix NullPointerException (NPE) in `TouchpadDebugViewTest`.

**Commit Link**: [Commit Link](https://cs.android.com/android/_/android/platform/frameworks/base/+/971e2ad244de47424891e19339cb34e0ac51d586)

