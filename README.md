# hand-tracking-ml
Module to help track hand with Computer Vision

### Hand Tracking

<hr>

<p align="center">
  <img width="640" height="360" src="https://github.com/infiniai-tech/infiniai/blob/main/Results/handtracking.png">
</p>

<pre>
from infiniai.HandTrackingModule import handDetector
import cv2
import time
import infiniai.HandTrackingModule as htm

pTime = 0
cTime = 0
cap = cv2.VideoCapture(0)
detector = handDetector()
while True:
    success, img = cap.read()
    img = detector.findHands(img)
    PosList = detector.findPosition(img)
    if len(PosList) != 0:
        print(PosList[4])

    cTime = time.time()
    fps = 1 / (cTime - pTime)
    pTime = cTime

    cv2.putText(img, str(int(fps)), (10, 70), cv2.FONT_HERSHEY_DUPLEX, 3, (255, 0, 0), 3)

    cv2.imshow("Webcam", img)
    cv2.waitKey(1)
cap.release()
cv2.destroyAllWindows()
</pre>

 

<hr>
