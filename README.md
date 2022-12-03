# dji-tello-cv2
Here is a simple example of how to write a Python program that uses the DJI Tello drone to track and follow people:

```
import cv2
from imutils.video import VideoStream
from tellopy import Tello

# Set the speed and distance of the drone
speed = 10
distance = 3

# Create a Tello object and connect to the drone
tello = Tello()
tello.connect()
tello.for_back_velocity = 0
tello.left_right_velocity = 0
tello.up_down_velocity = 0
tello.yaw_velocity = 0
tello.speed = 0

# Start the video stream
vs = VideoStream(src=0).start()

# Loop until the user presses a key
while True:
  # Get the frame from the video stream
  frame = vs.read()

  # Convert the frame to grayscale
  gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

  # Detect faces in the frame using Haar cascades
  faces = face_cascade.detectMultiScale(gray, 1.3, 5)

  # Loop through the detected faces
  for (x, y, w, h) in faces:
    # Calculate the center of the face
    face_center = (x + w // 2, y + h // 2)

    # Calculate the distance of the face from the center of the frame
    dx = face_center[0] - frame.shape[1] // 2
    dy = face_center[1] - frame.shape[0] // 2

    # Check if the face is within the specified distance from the center
    if abs(dx) < distance and abs(dy) < distance:
      # Move the drone in the direction of the face
      tello.for_back_velocity = speed * dy
      tello.left_right_velocity = speed * dx
      tello.up_down_velocity = 0
      tello.yaw_velocity = 0
    else:
      # Stop
```



# dji-tello-cv2 - Python program that uses the DJI Tello drone to dodge objects:

```
import cv2
from imutils.video import VideoStream
from tellopy import Tello

# Set the speed and distance of the drone
speed = 10
distance = 10

# Create a Tello object and connect to the drone
tello = Tello()
tello.connect()
tello.for_back_velocity = 0
tello.left_right_velocity = 0
tello.up_down_velocity = 0
tello.yaw_velocity = 0
tello.speed = 0

# Start the video stream
vs = VideoStream(src=0).start()

# Loop until the user presses a key
while True:
  # Get the frame from the video stream
  frame = vs.read()

  # Convert the frame to grayscale
  gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

  # Detect edges in the frame using the Canny algorithm
  edges = cv2.Canny(gray, 100, 200)

  # Find the contours in the frame
  _, contours, _ = cv2.findContours
```
